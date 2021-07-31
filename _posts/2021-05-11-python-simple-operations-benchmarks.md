---
layout: post
title:  'Python Simple Operations Benchmarks'
date:   2021-05-11 13:00:00 +0300
categories: post
author: Slava Spetsyian
email: slava@spetsyian.com
excerpt: 
type: blogpost
lang: en
---

It always worth checking the speed of some simple operations in order to make your application faster.

Let's compare a number of  approaches which may help accelerate your python scripts. 

__Note:__ presented benchmarks are run on Apple 2020 M1 Macbook Pro in Python 3.9 and may vary depending on runtime, configuration and hardware of the working machine. 

### List `append` vs `__add__`

There are at least two approaches to add value to a list: via `append` method and using __add__ dunder method. If you are new python or want to recall some knowleadge on dunder method, here is a [short article](https://builtin.com/data-science/dunder-methods-python) and here is Python documentation.

Simply say, we have an empty list `[]` and want to add `1` to it and get `[1]` in the result.

```python

# Variables first_approach and second_approach 
# are strings that are executed by timeit.timeit

>>> first_approach = """
x = []
x += [1]
"""

>>> timeit.timeit(first_approach, number=10_000_000)
0.496369082999081

>>> second_approach = "[].append([1])"

>>> timeit.timeit(second_approach, number=10_000_000)
0.5600485420000041

>>> third_approach = "[].extend([[1]])"

>>> timeit.timeit(third_approach, number=10_000_000)
0.7181027080005151
```

Even though we initialized a variable `x` in the first approach, it is still able to run faster then the `append` method.




