# 🧩 Bit Manipulation – Theory & Problems

Bit manipulation is the process of performing operations directly on the **bits** (binary representation) of numbers. It is very efficient and commonly used in competitive programming, low-level programming, and optimization problems.

---

## 📘 1. Introduction to Bit Manipulation

* A **bit** is the smallest unit of data in computing, having a value of either **0** or **1**.
* Numbers are stored in **binary form** (base 2).
* Common bitwise operators in Python:

  * `&` → Bitwise AND
  * `|` → Bitwise OR
  * `^` → Bitwise XOR
  * `~` → Bitwise NOT
  * `<<` → Left Shift
  * `>>` → Right Shift

---

## ✅ 2. Check if the i-th bit is set or not

**Problem:** Given a number `n` and a position `i`, check whether the `i-th` bit (0-indexed from right) is set (`1`) or not (`0`).

### 🔹 Explanation

* Create a mask with `1 << i` (shifts `1` to the `i-th` position).
* Perform `n & mask`.
* If the result is non-zero, the bit is set.

### 🔹 Python Code

```python
def is_ith_bit_set(n, i):
    mask = 1 << i
    return (n & mask) != 0

# Example
n, i = 10, 1  # binary 1010 → 1st bit is set
print(is_ith_bit_set(n, i))  # True
```

---

## ✅ 3. Check if a number is odd or not

**Problem:** Determine if a number is odd using bit manipulation.

### 🔹 Explanation

* In binary, odd numbers always have the **last bit (0-th)** set (`1`).
* Check `(n & 1)`.

### 🔹 Python Code

```python
def is_odd(n):
    return (n & 1) == 1

# Example
print(is_odd(7))  # True
print(is_odd(8))  # False
```

---

## ✅ 4. Check if a number is power of 2 or not

**Problem:** Determine if `n` is a power of 2.

### 🔹 Explanation

* A power of 2 has exactly **one set bit** in binary.
* Trick: `n & (n-1) == 0` if `n` is a power of 2 (and `n > 0`).

### 🔹 Python Code

```python
def is_power_of_two(n):
    return n > 0 and (n & (n - 1)) == 0

# Example
print(is_power_of_two(16))  # True
print(is_power_of_two(18))  # False
```

---

## ✅ 5. Count the number of set bits

**Problem:** Count how many `1`s are present in the binary representation of `n`.

### 🔹 Explanation

* Repeatedly check the last bit and shift right.
* Or use Brian Kernighan’s algorithm: repeatedly unset the rightmost set bit.

### 🔹 Python Code

```python
def count_set_bits(n):
    count = 0
    while n:
        n &= (n - 1)  # removes the rightmost set bit
        count += 1
    return count

# Example
print(count_set_bits(29))  # binary 11101 → 4 set bits
```

---

## ✅ 6. Set/Unset the rightmost unset bit

**Problem:** Modify `n` such that its rightmost unset (`0`) bit becomes set (`1`).

### 🔹 Explanation

* Rightmost unset bit → `~n & (n+1)`
* To **set** it: `n | (n+1)`
* To **unset** it: `n & (n+1)`

### 🔹 Python Code

```python
def set_rightmost_unset_bit(n):
    return n | (n + 1)

def unset_rightmost_unset_bit(n):
    return n & (n + 1)

# Example
print(bin(set_rightmost_unset_bit(10)))   # 1010 -> 1011 (11)
print(bin(unset_rightmost_unset_bit(10))) # 1010 -> 1000 (8)
```

---

## ✅ 7. Swap two numbers (without temp variable)

**Problem:** Swap two integers using bit manipulation.

### 🔹 Explanation

* Use XOR:

  * `a = a ^ b`
  * `b = a ^ b`
  * `a = a ^ b`

### 🔹 Python Code

```python
def swap(a, b):
    a = a ^ b
    b = a ^ b
    a = a ^ b
    return a, b

# Example
x, y = 5, 7
x, y = swap(x, y)
print(x, y)  # 7 5
```

---

# 🎯 Summary

| Problem                   | Key Trick                    |         |
| ------------------------- | ---------------------------- | ------- |
| Check i-th bit            | `(n & (1 << i)) != 0`        |         |
| Odd or Even               | `(n & 1)`                    |         |
| Power of 2                | `n > 0 and (n & (n-1)) == 0` |         |
| Count set bits            | `n &= (n-1)` loop            |         |
| Set rightmost unset bit   | \`n                          | (n+1)\` |
| Unset rightmost unset bit | `n & (n+1)`                  |         |
| Swap numbers              | XOR swap                     |         |

---

👉 This covers the **basic bit manipulation problems** with explanations and Python solutions.
