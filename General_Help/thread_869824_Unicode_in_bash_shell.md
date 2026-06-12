---
title: "Unicode in bash shell ?"
date: 2008-07-25
forum: General Help
---

### Post by brijith on 2008-07-25
Hai Friends,

How to print Unicode Character in a terminal Using Bash Script ?

[COLOR="Red"]**Thanks**[/COLOR]

---

### Post by pauper on 2008-07-25
```
man bash
```

370g

> \nnn   the eight-bit character whose value is the octal value nnn (one to three digits)
\xHH   the eight-bit character whose value is the hexadecimal value HH (one or two hex digits)

An example:

% (percent symbol) U+0025, Oct 045

```
echo $'\x25'
echo $'\045'
awk '{if($4=/mAh/)rc=$3}END{print((rc*100)/4800)"\x25"}' /proc/acpi/battery/BAT1/state
awk '{if($4=/mAh/)rc=$3}END{print((rc*100)/4800)"\045"}' /proc/acpi/battery/BAT1/state
awk '{if($4=/mAh/)rc=$3}END{print((rc*100)/4800)"%"}' /proc/acpi/battery/BAT1/state
```

You can type symbols right in terminal by pressing Alt-<key> or Alt-Shift-<key>:

£ -- Alt-Shift-3
&#8364; -- Alt-Shift-4
¥ -- Alt-Shift-5
ß -- Alt-Shift--
± -- Alt-1
÷ -- Alt-w
× -- Alt-Shift-w
¹ -- Alt-9
² -- Alt-2
³ -- Alt-3
¼ -- Alt-Shift-,
½ -- Alt-=
¾ -- Alt-Shift-.
» -- Alt-;
« -- Alt-Shift-=
§ -- Alt-'
® -- Alt-.
© -- Alt-Shift-0
° -- Alt-0
¡ -- Alt-Shift-1
¿ -- Alt-Shift-/

Note: This is not a complete list.

---

### Post by pauper on 2008-07-25
Some clarification is due.

1) bash shell
[list][*]Only these 94 ASCII characters can be represented with "\nnn" or "\xHH":

!"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijkl
mnopqrstuvwxyz{|}~ [indent]# [033-126][/indent]

The following special characters you type via Alt-<key> and
Alt-Shift-<key> but [highlight]not[/highlight] their [highlight]hexadecimal[/highlight] or [highlight]octal[/highlight] numbers. 

¡¢£¤¥¦§¨©ª«¬®¯°±²³´µ¶·¸¹º»¼½¾¿ÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖ×ØÙÚÛÜÝÞßàáâãäåæçèéêëìí
îïðñòóôõö÷øùúûüýþÿ [indent]# [161-255][/indent]

[*]You can use <Compose key><key><key>, i.e. <Compose key><+><-> -- ±.

```
less /usr/share/X11/locale/en_US.UTF-8/Compose
```[/list]
Note: Keep in mind though, if you are going to redirect output from bash script
to some GUI environment, you *might* need to use escapes ("\nnn" or "\xHH") for
# [161-255] characters.

2) gedit
[list][*]Use <Ctrl><Shift><u><Unicode number><Enter>
[*]<Compose key><key><key>.[/list]
A lot more characters are supported.

3) Vim (Insert mode)
[list][*] Press Ctrl-v {char} {value};
```

 +---------------+--------------+----------------+------------------------+
 | first char    |  mode        | max nr of chars|  max value             | 
 +---------------+--------------+----------------+------------------------+
 | (none)        |  decimal     |      3         |  255                   |
 | o or O        |  octal       |      3         |  377 (255)             |
 | x or X        |  hexadecimal |      2         |  ff  (255)             |
 | u             |  hexadecimal |      4         |  ffff (65535)          |
 | U             |  hexadecimal |      8         |  7fffffff (2147483647) |
 +---------------+--------------+----------------+------------------------+

```
[*] Press Ctrl-k {char1} {char2}, where {char1} is a special key;
```

 +-------------------+--------+------------------------------------+
 |  char name        |  char1 | meaning                            |
 +-------------------+--------+------------------------------------+
 |  Exclamation mark |  !     | Grave                              |
 |  Apostrophe       |  '     | Acute accent                       |
 |  Greater-Than sign|  >     | Circumflex accent                  |
 |  Question Mark    |  ?     | tilde                              |
 |  Hyphen-Minus     |  -     | Macron                             |
 |  Left parenthesis |  (     | Breve                              |
 |  Full Stop        |  .     | Dot Above                          |
 |  Colon            |  :     | Diaeresis                          |
 |  Comma            |  ,     | Cedilla                            |
 |  Underline        |  _     | Underline                          |
 |  Solidus          |  /     | Stroke                             |
 |  Quotation mark   |  "     | Double acute accent                |
 |  Semicolon        |  ;     | Ogonek                             |
 |  Less-Than sign   |  <     | Caron                              |
 |  Zero             |  0     | Ring above                         |
 |  Two              |  2     | Hook                               |
 |  Nine             |  9     | Horn                               |
 |                   |        |                                    |
 |  Equals           |  =     | Cyrillic                           |
 |  Asterisk         |  *     | Greek                              |
 |  Percent sign     |  %     | Greek/Cyrillic special             |
 |  Plus             |  +     | smalls: Arabic, capitals: Hebrew   |
 |  Three            |  3     | some Latin/Greek/Cyrillic letters  |
 |  Four             |  4     | Bopomofo                           |
 |  Five             |  5     | Hiragana                           |
 |  Six              |  6     | Katakana                           |
 +-------------------+--------+------------------------------------+

``` 
[*] <Compose key><key><key>[/list]

---

