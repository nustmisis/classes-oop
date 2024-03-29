# Задание "Комплексные числа"

## Теоретический минимум

Пусть $x = a + bi$ и $y = c + di$ &mdash; комплексные числа, $r$ &mdash; вещественное число, тогда операции над $x$, $y$ и $r$ представимы так:

#### Сложение

$$
\begin{align*}
x + y &= (a + bi) + (c + di) \\
&= (a + c) + (b + d)i \\
\end{align*}
$$

$$
\begin{align*}
x + r &= (a + bi) + (r + 0i) \\
&= (a + r) + bi \\
\end{align*}
$$

#### Вычитание

$$
\begin{align*}
x - y &= (a + bi) - (c + di) 
\\ &= (a - c) + (b - d)i \\
\end{align*}
$$

$$
\begin{align*}
x - r &= (a + bi) - (r + 0i) 
\\ &= (a - r) + bi
\end{align*}
$$

#### Произведение

$$
\begin{align*}
x \cdot y &=  (a + bi) \cdot (c + di) \\
&= ac + bci + adi + bdi^2 \\
&= (ac - bd) + (bc + ad)i
\end{align*}
$$

$$
x \cdot r = (a + bi) \cdot r = ar + bri
$$

#### Деление

$$
\begin{align*}
\frac{x}{y} &= \frac{a + bi}{c + di} \\   
&= \frac{(a + bi)(c - di)}{(c + di)(c - di)} \\
&= \frac{(a + bi)(c - di)}{c^2 + d^2} \\
&= \frac{ac + bd}{c^2 + d^2} + \frac{bc - ad}{c^2 + d^2}i
\end{align*}
$$

$$
\frac{x}{r} = \frac{a + bi}{r} = \frac{a}{r} + \frac{b}{r}i
$$

## Подсказки

В рамках этого задания вам достаточно представлять комплексное число как пару вещественных чисел, а все операции над ним &mdash; как операции над парами чисел.

---

Чтобы ваш класс соответствовал всем требованиям, он должен реализовывать следующие методы:

- `__init__` для создания экземпляров ("конструктор");
- `__add__`, `__sub__`, `__mul__`, `__truediv__` для поддержки арифметики;
- `__radd__`, `__rsub__`, `__rmul__`, `__rtruediv__` для поддержки арифметики, когда экземпляр класса находится справа от оператора;
- `__eq__` для сравнений (`__ne__` по умолчанию вернет результат, обратный результату `__eq__`);
- `__str__` для преобразования экземпляра в строку.

Если после запуска `pytest` вы получаете ошибку вида `TypeError: unsupported operand type(s) for *: 'int' and 'Complex'`, убедитесь, что вы корректно реализовали соответствующий метод класса `Complex` (в этом случае `__rmul__`). 

---

Обратите внимание, что операции, где экземпляр Complex находится справа от оператора, требуют наличия отдельного метода с префиксом `r`: 

```python
c, r = Complex(1, 2), 1

c + r == Complex.__add__(c, r)
r + c == Complex.__radd__(c, r)
```

---

В этом задании вам потребуется по-разному обрабатывать аргументы методов в зависимости от их типа. Для этого пользуйтесь встроенной функцией [`isinstance()`](https://docs.python.org/3/library/functions.html#isinstance). Например, `isinstance(x, (int, float))` вернет `True` только если `x` имеет тип `int` или `float`.

---

Вы можете протестировать свое решение, выполнив команду `pytest` в этой папке (при условии установленного модуля pytest), или в прямо в интерпретаторе Python. Для этого импортируйте класс `Complex` из модуля `tasks.complex`, после чего вы сможете выполнять создавать экземпляры класса и производить операции с ними в интерактивном режиме.

---

Документация файла [./tasks/complex.py](./tasks/complex.py) на самом деле тоже является [тестом](https://docs.python.org/3/library/doctest.html) для вашего класса. Для его запуска вызовите команду ниже:

```sh
python3 -m doctest tasks/complex.py
```

Этот тест не является обязательным для выполнения задания, однако валидное решение будет проходить его без ошибок.