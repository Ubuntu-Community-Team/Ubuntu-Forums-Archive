---
title: "Epson TX105 printer ink level"
date: 2009-07-01
forum: Hardware
---

### Post by zepita on 2009-07-01
Hi,

I have an Epson Stylus TX105 multifunction printer installed in ubuntu 9.04 i386 using CUPS+Gutenprint 5.2.3
It has no problems to scan or print, but when going to ink level, it just says that "marker levels are not reported by this printer"

I have tried with inkblot but it says the same.

Is there any way to check the ink levels of this printer?


Thanks in advance.

---

### Post by zepita on 2009-07-02
anyone?

---

### Post by zepita on 2009-07-02
I have just fixed the issue by typing

```
$ sudo escputil -ir /dev/usblp?
[sudo] password for mleyes: 
Escputil version 5.2.3, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

         Ink color       Percent remaining
              Cyan                     100
            Yellow                     100
           Magenta                     100
             Black                      78

```

---

