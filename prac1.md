# Практическое занятие №1. Введение, основы работы в командной строке

Нестеров Глеб Александрович , РТУ МИРЭА

Научиться выполнять простые действия с файлами и каталогами в Linux из командной строки. Сравнить работу в командной строке Windows и Linux.

## Задача 1

Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).
```
awk -F' ' '{print $2, $1, $3}' /etc/protocols | sort -n -k1 | tail -n 5
```
![изображение](https://github.com/user-attachments/assets/917abfa8-c098-4e85-aa73-3ae713abfbfd)


## Задача 2

Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов.
```
awk -F' ' '{print $2, $1, $3}' /etc/protocols | sort -n -k1 | tail -n 5
```
![изображение](https://github.com/user-attachments/assets/43aa2ec8-e1c2-4493-bf47-51d69be265d4)


## Задача 3

Написать программу banner средствами bash для вывода текстов.

```
#!/bin/bash

text=$*
length=${#text}

for i in $(seq 1 $((length + 2))); do
    line+="-"
done

echo "+${line}+"
echo "| ${text} |"
echo "+${line}+"
```
![изображение](https://github.com/user-attachments/assets/72700e36-8db8-4281-8356-a626fa0a8bbf)

## Задача 4

Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).

Пример для hello.c:

```
#!/bin/bash

file="hello.c"

identifiers=$(grep -o -E '\b[a-zA-Z_]\w*\b' "$file")
unique_identifiers=$(echo "$identifiers" | sort | uniq)

echo "$unique_identifiers"
```

![изображение](https://github.com/user-attachments/assets/0e70210a-1e40-47b2-9d18-3746b523b529)


Общие сведения

https://ru.wikipedia.org/wiki/Интерфейс_командной_строки
https://nullprogram.com/blog/2020/08/01/
https://habr.com/ru/post/150950/

Стандарты

https://www.gnu.org/prep/standards/standards.html#Command_002dLine-Interfaces
https://www.gnu.org/software/libc/manual/html_node/Argument-Syntax.html
https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap12.html

Реализация разбора опций

Питон

https://docs.python.org/3/library/argparse.html#module-argparse
https://click.palletsprojects.com/en/7.x/
