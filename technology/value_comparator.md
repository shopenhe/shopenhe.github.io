# Value Comparator

>**Tags**: Java<br>**Last Modify**: 2024/01/31 15:00

## Question

```
a > b => a - b > 0 // ?
```

## Answer

```
a > b // No Problem
a - b > 0 // Problem: numeric overflow risk
```

For example:

```
Integer.MAX_VALUE > -1 // true
Integer.MAX_VALUE - (-1) > 0 // false
```

## Thinking

It's a **interesting** question, we should be **careful**. When we compare values, `Comparator` is suggested, such as `Integer.compare(x, y)` in Java:

```java
/**
 * Compares two {@code int} values numerically.
 * The value returned is identical to what would be returned by:
 * <pre>
 *    Integer.valueOf(x).compareTo(Integer.valueOf(y))
 * </pre>
 *
 * @param  x the first {@code int} to compare
 * @param  y the second {@code int} to compare
 * @return the value {@code 0} if {@code x == y};
 *         a value less than {@code 0} if {@code x < y}; and
 *         a value greater than {@code 0} if {@code x > y}
 * @since 1.7
 */
public static int compare(int x, int y) {
  return (x < y) ? -1 : ((x == y) ? 0 : 1);
}
```
