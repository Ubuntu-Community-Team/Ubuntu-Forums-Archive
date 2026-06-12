---
title: "i need help with ,exe files"
date: 2008-07-14
forum: General Help
---

### Post by rayz321 on 2008-07-14
ok here is my problem whenever i download a .exe file it will not open i have wine but that still will not work this is the file that i download and it will not work i hit open with wine then nothin opens i do extract it to this is the file i am trying to get to work []("http://www.autofighter.org/download.php?file=AutoTalkerX.zip&name=AutoTalker%20Pro%20X&id=AutoTalkerX")

---

### Post by Het Irv on 2008-07-14
Wine may not work with your program, to check compatiblity go to [www.appdb.org](www.appdb.org) and seach for your program.

---

### Post by avtolle on 2008-07-14
Generally, exe files will not open in Linux; most exe files are Windows files, a completely different O/S from Linux (and from Mac OX X, e.g.). An exception is provided by Wine, with which I've no experience. It these files are important to you, then you need to either dual boot Windows and Linux, or run Windows from a virtual machine installed under Linux.

---

### Post by mzhb@mac.com on 2008-07-14
what is the output when you use wine to that file?

---

### Post by rayz321 on 2008-07-14
i do not know it might be (wine start /unix %f) or how do you tell?

---

### Post by tramir on 2008-07-14
Start a terminal, go to the folder where you downloaded the .exe (cd path/to/exe), and type 
```
wine name_of_exe
```

(replace "path/to/exe" with the folder where you downloaded the file and "name_of_exe" with the filename of the exe file, including the extension). Paste here the output of that command.

---

