## Unsafe介绍及作用
## Unsafe对象的获取
-Xbootclasspath/a:D:\work\projects\test\target\test-1.0-SNAPSHOT.jar

```java
package com.star95.study;

import java.lang.reflect.Field;

import sun.misc.Unsafe;

/**
 * @author hemingzhun
 * @date 2020/3/30 8:55
 */
public class Test {
    public static void main(String[] args) throws Exception {
        // 1 Unsafe unsafe = UnsafeUtil.getUnsafe();

        // 2
        // Constructor constructor = Unsafe.class.getDeclaredConstructors()[0];
        // constructor.setAccessible(true);
        // Unsafe unsafe = (Unsafe)constructor.newInstance();

        // 3
        Unsafe unsafe = getUnsafe();
        Test t = new Test();
        System.out.println("aa");
        System.out.println(unsafe.getInt(t, unsafe.objectFieldOffset(Test.class.getDeclaredField("a"))));;
        System.out.println(Unsafe.ARRAY_BYTE_BASE_OFFSET);
        System.out.println(Unsafe.ARRAY_INT_BASE_OFFSET);
        System.out.println(Unsafe.ARRAY_INT_INDEX_SCALE);
        System.out.println(Unsafe.ARRAY_LONG_INDEX_SCALE);
        System.out.println(Unsafe.ARRAY_OBJECT_BASE_OFFSET);
        System.out.println(Unsafe.ARRAY_OBJECT_INDEX_SCALE);
        System.out.println(Unsafe.ARRAY_BOOLEAN_INDEX_SCALE);
        System.out.println(Unsafe.ARRAY_BYTE_INDEX_SCALE);
        System.out.println(Unsafe.ARRAY_CHAR_INDEX_SCALE);

    }

    private static Unsafe getUnsafe() {
        try {
            Field field = Unsafe.class.getDeclaredField("theUnsafe");
            field.setAccessible(true);
            System.out.println("---------");
            return (Unsafe)field.get(null);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return null;
    }

    private int a = 12;
}

```
## Unsafe方法介绍
## Unsafe使用案例
## Unsafe与CAS