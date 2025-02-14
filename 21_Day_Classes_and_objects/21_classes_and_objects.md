<div align="center">
  <h1> 30 Дней Python: День 21 - Классы и объекты</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

<sub>Автор:
<a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
<small>Второе издание: Июль, 2021</small>
</sub>

</div>

[<< День 20](../20_Day_Python_package_manager/20_python_package_manager.md) | [День 22 >>](../22_Day_Web_scraping/22_web_scraping.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 День 21](#-день-21)
  - [Классы и объекты](#классы-и-объекты)
    - [Создание класса](#создание-класса)
    - [Создание объекта](#создание-объекта)
    - [Конструктор класса](#конструктор-класса)
    - [Методы объекта](#методы-объекта)
    - [Методы объекта со значением по умолчанию](#методы-объекта-со-значением-по-умолчанию)
    - [Методы для изменения значений по умолчанию](#методы-для-изменения-значений-по-умолчанию)
    - [Наследование](#наследование)
    - [Переопределение родительских методов](#переопределение-родительских-методов)
  - [💻 Упражнения: День 21](#-упражнения-день-21)
    - [Упражнения: Уровень 1](#упражнения-уровень-1)
    - [Упражнения: Уровень 2](#упражнения-уровень-2)
    - [Упражнения: Уровень 3](#упражнения-уровень-3)

# 📘 День 21

## Классы и объекты

Python - объектно-ориентированный язык программирования. Всё в Python это объекты, со своими свойствами и методами. Числа, строки, списки, словари, кортежи, множества и т.д., используемые в программах, это объекты соответствующих встроенных классов. Мы создаем класс, чтобы создавать объекты. Класс похож на конструктор объекта, или на "кальку" для создания объектов. В виде класса мы создаем образец, по которому создаются объекты. Класс определяет аттрибуты и поведение объектов, в то время как сам объект представляет свой класс.

Мы работали с классами и объектами с самого начала челленджа, даже это не осознавая. Каждый элемент в программе на Python это объект класса.
Давайте убедимся, что все в python это классы:

```py
Python 3.10.9 (tags/v3.10.9:1dd9be6, Dec  6 2022, 20:01:21) [MSC v.1934 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> num = 10                                                          
>>> type(num)
<class 'int'>
>>> string = 'строка'
>>> type(string)
<class 'str'>
>>> boolean = True
>>> type(boolean)
<class 'bool'>
>>> lst = []
>>> type(lst)
<class 'list'>
>>> tpl = ()
>>> type(tpl)
<class 'tuple'>
>>> set1 = set()
>>> type(set1)
<class 'set'>
>>> dct = {}
>>> type(dct)
<class 'dict'>
```

### Создание класса

Для создания класса используется ключевое слово **class**, далее следует название класса и двоеточие. Название класса пишется в **CamelCase** (ГорбатыйРегистр).

```sh
# синтаксис
class ClassName:
    здесь будет код
```

**Пример:**

```py
class Person:
    pass
print(Person)
```

```sh
<class '__main__.Person'>
```

### Создание объекта

Мы можем создать объект, вызвав класс.

```py
p = Person()
print(p)
```

```sh
<__main__.Person object at 0x000001929043F940>
```

### Конструктор класса

В примере выше мы создали объект класса Person. Однако, класс без конструктора не очень то полезен в настоящих приложениях. Давайте используем функцию конструктора, чтобы сделать наш класс более полезным. Как функции конструкторы в Java или JavaScript, в Python также есть встроенная функция конструктор **__init__**(). Функция конструктор **__init__** принимает параметр self, который ссылается на текущую сущность класса.

**Примеры:**

```py
class Person:
    def __init__ (self, name):
        # self позволяет прикрепить параметр к объекту класса
        self.name = name

p = Person('Asabeneh')
print(p.name)
print(p)
```

```sh
# вывод результата
Asabeneh
<__main__.Person object at 0x2abf46907e80>
```

Давайте добавим больше параметров в функцию конструктор.

```py
class Person:
    def __init__(self, firstname, lastname, age, country, city):
        self.firstname = firstname
        self.lastname = lastname
        self.age = age
        self.country = country
        self.city = city


p = Person('Иван', 'Петров', 250, 'Россия', 'Урюпинск')
print(p.firstname)
print(p.lastname)
print(p.age)
print(p.country)
print(p.city)
```

```sh
# вывод результата
Иван
Петров
250
Россия
Урюпинск
```

### Методы объекта

Объекты могут иметь методы. Методы - это функции, которые принадлежат объекту.

**Пример:**

```py
class Person:
    def __init__(self, firstname, lastname, age, country, city):
        self.firstname = firstname
        self.lastname = lastname
        self.age = age
        self.country = country
        self.city = city
    def person_info(self):
        return f'{self.firstname} {self.lastname} - это человек, которому {self.age} лет. Он живет в городе {self.city}, {self.country}'

p = Person('Иван', 'Петров', 250, 'Россия', 'Урюпинск')
print(p.person_info())
```

```sh
# вывод результата
Иван Петров - это человек, которому 250 лет. Он живет в городе Урюпинск, Россия
```

### Методы объекта со значением по умолчанию

Иногда вам может понадобиться указать значения по умолчанию для методов объектов. Если мы указываем для параметров конструктора значения по умолчанию, мы можем избежать ошибок, связанных с созданием объекта класса без параметров. Давайте взглянем, как это выглядит:

**Пример:**

```py
class Person:
    def __init__(self, firstname='Иван', lastname='Петров', age=250, country='Россия', city='Урюпинск'):
        self.firstname = firstname
        self.lastname = lastname
        self.age = age
        self.country = country
        self.city = city
        self.skills = []

    def person_info(self):
        return f'{self.firstname} {self.lastname} - это человек, которому {self.age} лет. Он живет в городе {self.city}, {self.country}.'

p1 = Person()
print(p1.person_info())
p2 = Person('Денис', 'Никифоров', 30, 'Россия', 'Пермь')
print(p2.person_info())
```

```sh
# вывод результата
Иван Петров - это человек, которому 250 лет. Он живет в городе Урюпинск, Россия.
Денис Никифоров - это человек, которому 30 лет. Он живет в городе Пермь, Россия.
```

Примечание переводчика: не следует делать значением по умолчанию пустой изменяемый объект (список, словарь), т.к. он будет создан в момент объявления метода и станет общим для всех будущих объектов класса, созданных со значением по умолчанию. Вы же не хотите, чтобы Иван Петров выучил Python, положил его в свой список self.skills, и Python автоматически оказался в списке self.skills У Дениса Никифорова, который ничего не изучал?

### Методы для изменения значений по умолчанию

В примере выше у конструктора класса Person параметры имели значение по умолчанию. В дополнение к этому у нас есть параметр навыки skills, к которому можно получить доступ с помощью методов. Давайте создадим метод add_skill, чтобы добавлять навыки в список навыков.

```py
class Person:
    def __init__(self, firstname='Иван', lastname='Петров', age=250, country='Россия', city='Урюпинск'):
        self.firstname = firstname
        self.lastname = lastname
        self.age = age
        self.country = country
        self.city = city
        self.skills = []

    def person_info(self):
        return f'{self.firstname} {self.lastname} - это человек, которому {self.age} лет. Он живет в городе {self.city}, {self.country}.'
    def add_skill(self, skill):
        self.skills.append(skill)

p1 = Person()
print(p1.person_info())
p1.add_skill('HTML')
p1.add_skill('CSS')
p1.add_skill('JavaScript')
p2 = Person('Денис', 'Никифоров', 30, 'Россия', 'Пермь')
print(p2.person_info())
print(p1.skills)
print(p2.skills)
```

```sh
# вывод результата
Иван Петров - это человек, которому 250 лет. Он живет в городе Урюпинск, Россия.
Денис Никифоров - это человек, которому 30 лет. Он живет в городе Пермь, Россия.
['HTML', 'CSS', 'JavaScript']
[]
```

### Наследование

С помощью наследования можно переиспользовать код из родительского класса. Наследование позволяет определить класс, который будет наследовать все методы и свойства от родительского класса. Родительский класс, или суперкласс (super), или базовый класс (base), это класс, который дает все свои методы и свойства. Дочерний класс - это класс, который наследует от другого, родительского класса.
Давайте создадим класс студент, отнаследовав его от класса Person.

```py
class Student(Person):
    pass


s1 = Student('Александр', 'Никитин', 30, 'Россия', 'Москва')
s2 = Student('Петр', 'Максимов', 28, 'Россия', 'Псков')
print(s1.person_info())
s1.add_skill('JavaScript')
s1.add_skill('React')
s1.add_skill('Python')
print(s1.skills)

print(s2.person_info())
s2.add_skill('Систематизирование')
s2.add_skill('Маркетинг')
s2.add_skill('Цифровой маркетинг')
print(s2.skills)

```

```sh
# вывод результата
Александр Никитин - это человек, которому 30 лет. Он живет в городе Москва, Россия.
['JavaScript', 'React', 'Python']
Петр Максимов - это человек, которому 28 лет. Он живет в городе Псков, Россия.
['Систематизирование', 'Маркетинг', 'Цифровой маркетинг']
```

Мы не определяли конструктор **__init__**() в дочернем классе. Но даже если его нет, мы имеем доступ ко всем свойствам родительского класса. Но если мы определим свой конструктор, мы можем получить доступ к свойствам родительского класса, вызывая _super_.  
Мы можем добавить новый метод в дочерний класс или можем переопределить методы родительского класса, создавая метод с тем же названием в дочернем классе. Когда мы добавляем функцию **__init__**(), дочерний класс перестает наследовать родительскую функцию **__init__**().

### Переопределение родительских методов

```py
class Student(Person):
    def __init__ (self, firstname='Иван', lastname='Петров',age=250, country='Россия', city='Урюпинск', gender='мужской'):
        self.gender = gender
        super().__init__(firstname, lastname,age, country, city)
    def person_info(self):
        gender = 'Он' if self.gender =='мужской' else 'Она'
        return f'{self.firstname} {self.lastname} - это человек, которому {self.age} лет. {gender} живет в городе {self.city}, {self.country}.'

s1 = Student('Петр', 'Максимов', 30, 'Россия', 'Псков','мужской')
s2 = Student('Лидия', 'Иванова', 28, 'Россия', 'Новосибирск', 'женский')
print(s1.person_info())
s1.add_skill('JavaScript')
s1.add_skill('React')
s1.add_skill('Python')
print(s1.skills)

print(s2.person_info())
s2.add_skill('Систематизирование')
s2.add_skill('Маркетинг')
s2.add_skill('Цифровой маркетинг')
print(s2.skills)
```

```sh
Петр Максимов - это человек, которому 30 лет. Он живет в городе Псков, Россия.
['JavaScript', 'React', 'Python']
Лидия Иванова - это человек, которому 28 лет. Она живет в городе Новосибирск, Россия.
['Систематизирование', 'Маркетинг', 'Цифровой маркетинг']
```

Мы можем использовать встроенную функцию super() или имя родительского класса Person, чтобы автоматически наследовать методы и свойства от родителя. В примере выше мы переопределили родительский метод. Дочерний метод имеет дополнительную возможность, он определяет пол, чтобы подставлять корректное местоимение (Он/Она).

🌕 Теперь вы полностью заряжены суперэнергией программирования. Пора выполнить несколько упражнений для мозга и мускулов.

## 💻 Упражнения: День 21

### Упражнения: Уровень 1

1. В Python есть модуль под названием _statistics_, и мы можем его использовать для статистических вычислений. Однако, чтобы научиться писать функции и их переиспользовать, давайте попробуем разработать программу, которая считает средние значения выборки (среднее арифметическое, медиану, моду) и характеристики изменчивости (разброс величин, дисперсия, стандартное отклонение). В дополнение к этому, найдите минимум, максимум, количество, персентиль и частотное распределение выборки. Создайте класс с названием Statistics и напишите все функции, которые будут делать статистические вычисления, в качестве методов класса Statistics. Ознакомьтесь с выводом результата ниже.

```py
ages = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

print('Количество:', data.count()) # 25
print('Сумма: ', data.sum()) # 744
print('Минимум: ', data.min()) # 24
print('Максимум: ', data.max()) # 38
print('Разброс величин: ', data.range()) # 14
print('Среднее арифметическое: ', data.mean()) # 30
print('Медиана: ', data.median()) # 29
print('Мода: ', data.mode()) # {'mode': 26, 'count': 5}
print('Стандартное отклонение: ', data.std()) # 4.2
print('Дисперсия: ', data.var()) # 17.5
print('Частотное распределение: ', data.freq_dist()) # [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

```sh
# вывод результата должен выглядеть примерно так:
print(data.describe())
Количество: 25
Сумма:  744
Минимум:  24
Максимум:  38
Разброс величин:  14
Среднее арифметическое:  30
Медиана:  29
Мода:  (26, 5)
Дисперсия:  17.5
Стандартное отклонение:  4.2
Частотное распределение: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

### Упражнения: Уровень 2

1. Создайте класс под названием PersonAccount. У него есть свойства firstname (имя), lastname (фамилия), incomes (доходы), expenses (расходы) и методы total_income (общие доходы), total_expense (общие расходы), account_info (информация о счете), add_income (добавить доход), add_expense (добавить расход) и account_balance (баланс счета). Доходы это множество доходов с их описанием, то же касается и расходов.

### Упражнения: Уровень 3

Примечание переводчика: задания в этом пункте отсутствуют. Вы можете попробовать добавить в класс PersonAccount свойство deposit, содержащее определенную сумму денег, и реализовать метод, позволяющий переводить эти деньги на deposit другого экземпляра класса следующим образом:
```python
account_1 = PersonAccount(deposit=1000)
account_2 = PersonAccount(deposit=0)
print(account_1.deposit)
print(account_2.deposit)
account_1.transfer_money(account_2, 1000)
print(account_1.deposit)
print(account_2.deposit)
```
```sh
1000
0
0
1000
```
Внутри метода transfer_money следует проверить, что на депозите есть большая или равная переводу сумма, а также, что переданный в метод account_2 является объектом класса PersonAccount (в этом поможет функция isinstance()). 

🎉 ПОЗДРАВЛЯЮ ! 🎉

[<< День 20](../20_Day_Python_package_manager/20_python_package_manager.md) | [День 22 >>](../22_Day_Web_scraping/22_web_scraping.md)
