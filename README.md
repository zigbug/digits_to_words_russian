# digits_to_words_russian

Flutter/Dart-пакет, переводящий число в его русское словесное обозначение:
**42 → «сорок два»**, **1001 → «одна тысяча один»**.

A Flutter/Dart package that converts a number into its Russian word form:
**42 → «сорок два»**, **1001 → «одна тысяча один»**.

[![Dart](https://img.shields.io/badge/Dart-2.18%2B-0175C2?logo=dart&logoColor=white)](https://dart.dev)
[![Flutter](https://img.shields.io/badge/Flutter-compatible-02569B?logo=flutter)](https://flutter.dev)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🇷🇺 Русский

### Описание

Пакет складывает число из разрядов (сотни, десятки, единицы) и подставляет правильные
русские формы с учётом рода и склонения:

- единицы в пределах тысячи/миллиарда: **один / одна**, **два / две**;
- склонение разрядов: **тысяча / тысячи / тысяч**, **миллион / миллиона / миллионов**,
  **миллиард / миллиарда / миллиардов**, **триллион / триллиона / триллионов**;
- особые формы для 11–19 («одиннадцать», «пятнадцать» …);
- корректные сотни и десятки («двести тридцать четыре»).

Диапазон: от 1 до **999 999 999 999 999** (999 триллионов). Более крупные числа
парсер не поддерживает — генерируется `DigitsToWordsRussianParserException`.

### Использование

```yaml
dependencies:
  digits_to_words_russian: ^0.0.1
```

```dart
import 'package:digits_to_words_russian/digits_to_words_russian.dart';

final parser = DigitsToWordsParser();

print(parser.toWords(number: 42).trim());        // сорок два
print(parser.toWords(number: 1001).trim());      // одна тысяча один
print(parser.toWords(number: 2021).trim());      // две тысячи двадцать один
print(parser.toWords(number: 2000).trim());      // две тысячи
print(parser.toWords(number: 1234567).trim());   // один миллион двести тридцать
                                                 // четыре тысячи пятьсот
                                                 // шестьдесят семь
print(parser.toWords(number: 999999999999999).trim());
// девятьсот девяносто девять триллионов ... девятьсот девяносто девять
```

### Ограничения

- Метод возвращает строку с **ведущим пробелом** — вызывайте `.trim()` перед
  выводом или сравнением.
- `toWords(number: 0)` возвращает пустую строку (текущая версия парсит только
  ненулевые числа).
- Отрицательные числа не поддерживаются.

### Структура проекта

```
digits_to_words_russian/
├── lib/
│   ├── digits_to_words_russian.dart  # DigitsToWordsParser.toWords()
│   └── exeption.dart                 # DigitsToWordsRussianParserException
├── example/                          # Flutter-пример приложения
├── LICENSE                           # MIT
├── README.md
└── pubspec.yaml
```

### Технологии

- **Dart** (код чисто Dart, Flutter-зависимость в `pubspec.yaml` для совместимости
  с Flutter-приложениями)
- Тест: `test/digits_to_words_russian_test.dart` (заготовка)

### Связанные проекты

Расширенная версия пакета с порядковыми числительными и датами
(`ordinalToWords`, `dateToWords`) — **[digits_to_words_russian_public](https://github.com/zigbug/digits_to_words_russian_public)**.

---

## 🇬🇧 English

### Overview

The package assembles a number from its digit groups (hundreds, tens, units) and
substitutes correct Russian word forms with gender and declension handled:

- units within a thousand/billion: **один / одна**, **два / две**;
- group declension: **тысяча / тысячи / тысяч**, **миллион / миллиона / миллионов**,
  **миллиард / миллиарда / миллиардов**, **триллион / триллиона / триллионов**;
- special forms for 11–19;
- correct hundreds and tens.

Range: 1 to **999,999,999,999,999** (999 trillions). Larger numbers are not
supported — `DigitsToWordsRussianParserException` is thrown.

### Usage

```yaml
dependencies:
  digits_to_words_russian: ^0.0.1
```

```dart
import 'package:digits_to_words_russian/digits_to_words_russian.dart';

final parser = DigitsToWordsParser();

print(parser.toWords(number: 42).trim());        // сорок два
print(parser.toWords(number: 1001).trim());      // одна тысяча один
print(parser.toWords(number: 2021).trim());      // две тысячи двадцать один
print(parser.toWords(number: 1234567).trim());   // один миллион двести тридцать
                                                 // четыре тысячи пятьсот
                                                 // шестьдесят семь
```

### Limitations

- The method returns a string with a **leading space** — call `.trim()`.
- `toWords(number: 0)` returns an empty string (the current version only parses
  non-zero numbers).
- Negative numbers are not supported.

### Project structure

```
digits_to_words_russian/
├── lib/
│   ├── digits_to_words_russian.dart  # DigitsToWordsParser.toWords()
│   └── exeption.dart                 # DigitsToWordsRussianParserException
├── example/                          # Flutter example app
├── LICENSE                           # MIT
├── README.md
└── pubspec.yaml
```

### Tech stack

- **Dart** (pure Dart code; the Flutter dependency in `pubspec.yaml` only keeps the
  package compatible with Flutter apps)

### Related projects

The extended version with ordinal numerals and dates
(`ordinalToWords`, `dateToWords`) —
**[digits_to_words_russian_public](https://github.com/zigbug/digits_to_words_russian_public)**.
