---
title: "File recovery - blackout"
date: 2008-08-23
forum: General Help
---

### Post by nikio on 2008-08-23
My Amule works with a temp folder on an ext2 partition
after a blackout i restarted the program and some of the downloads were disappeared
with the graphical file browser no files were shown in the temporary folder, but with a 
```
ls -l
``` 
command this was the result:
> nik@nik-desktop:/media/AduTemp$ ls -l
ls: cannot access 023.part.met.bak: Input/output error
ls: cannot access 023.part.met: Input/output error
ls: cannot access 009.part.met.bak: Input/output error
ls: cannot access 021.part.met: Input/output error
ls: cannot access 021.part.met.bak: Input/output error
ls: cannot access 012.part.met: Input/output error
ls: cannot access 011.part.met.bak: Input/output error
ls: cannot access 012.part.met.bak: Input/output error
ls: cannot access 011.part.met: Input/output error
total 710688
-rw-r--r-- 1 nik  nik  366030848 2008-08-23 20:35 009.part
-????????? ? ?    ?            ?                ? 009.part.met.bak
-rw-r--r-- 1 nik  nik  365803520 2008-08-23 20:36 011.part
-????????? ? ?    ?            ?                ? 011.part.met
-????????? ? ?    ?            ?                ? 011.part.met.bak
-rw-r--r-- 1 nik  nik  366282752 2008-08-23 20:34 012.part
-????????? ? ?    ?            ?                ? 012.part.met
-????????? ? ?    ?            ?                ? 012.part.met.bak
-rw-r--r-- 1 nik  nik  365936640 2008-08-23 20:35 021.part
-????????? ? ?    ?            ?                ? 021.part.met
-????????? ? ?    ?            ?                ? 021.part.met.bak
-rw-r--r-- 1 nik  nik  366407680 2008-08-23 20:35 023.part
-????????? ? ?    ?            ?                ? 023.part.met
-????????? ? ?    ?            ?                ? 023.part.met.bak
drwx------ 2 root root     16384 2008-06-26 00:48 lost+found
drwxr-xr-x 2 nik  nik       4096 2008-08-23 21:17 pro


I need to recover all the files with the input output error (the .met files) in order to recover the associated downloaded data (the .part files)
is there any command or program that could help?

---

