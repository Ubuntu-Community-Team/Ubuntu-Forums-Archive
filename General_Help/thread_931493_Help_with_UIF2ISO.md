---
title: "Help with UIF2ISO"
date: 2008-09-27
forum: General Help
---

### Post by phazer_34 on 2008-09-27
Well i have uif2iso insatll but when i try to convert i got this:

-----------------------------
warrens@warrens-desktop:~$ uif2iso Windows.uif Windows.iso

UIF2ISO 0.1.6
by Luigi Auriemma
e-mail: [email]aluigi@autistici.org[/email]
web:    aluigi.org

- open Windows

Error: No such file or directory
warrens@warrens-desktop:~$ 
-------------------------------

What do i do? Kinda new to linux so any help would be helpful

---

### Post by ashmew2 on 2008-09-27
Where have you put ur Windows.uif file ? If it is on your desktop , you need to first change directory to desktop.. For that do in the terminal :
```

cd ~/Desktop

```
 Now you can go ahead and run the conversion :)

Plus , Always Remeber Linux/Unix is case sensitive..meaning that windows.uif is different from Windows.uif which is again different from WINDOWS.uif..

---

### Post by BCtom on 2009-02-19
I would like to add one more thing regarding UIF2ISO's operation. Because of the case sensitive issue with LINUX vrs Window$, and the way MS users like to name their files, I found that I have to put in parentheses if the file name if it containes: spaces, peroids, plus-signs, brackets and so on. 

Eg: blah blah - v2.34.0.1+b [super poster].UIF, would be "blah blah - v2.34.0.1+b [super poster].UIF" your_file_name

You don't need to put a file exstention after your file name, i.e. ".iso". 

The command line would be 

> uif2iso "blah blah - v2.34.0.1+b [super poster].UIF" your_file_nameI hope that this saves someone a lot of time from blinldy typing in commands all day.

---

