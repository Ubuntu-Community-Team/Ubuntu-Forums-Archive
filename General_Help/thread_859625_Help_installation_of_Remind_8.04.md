---
title: "Help installation of Remind 8.04"
date: 2008-07-14
forum: General Help
---

### Post by Otto-C on 2008-07-14
Having trouble installing the program Remind. Have done
sudo apt-get install remind. Cannot figure out how to run it.
Help please.

tia
otto-c

---

### Post by sayakb on 2008-07-14
At a terminal, type in:
```
remind
```
If it fails, try to find out the path by typing in:
```
which remind
```

---

### Post by Otto-C on 2008-07-15
This is what I get. Can't get to the GUI etc. Thanks

otto@desktop:~$ remind
The program 'remind' is currently not installed.  You can install it by typing: sudo apt-get install remind
bash: remind: command not found
otto@desktop:~$ sudo apt-get install remind
[sudo] password for otto: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  tk8.4 wish wyrd
The following NEW packages will be installed:
  remind
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/212kB of archives.
After this operation, 565kB of additional disk space will be used.
Selecting previously deselected package remind.
(Reading database ... 141060 files and directories currently installed.)
Unpacking remind (from .../remind_03.00.24-4_i386.deb) ...
Setting up remind (03.00.24-4) ...

otto@desktop:~$ remind
Can't access file: `/home/otto/.reminders'.
otto@desktop:~$ which remind
/usr/bin/remind
otto@desktop:~$

---

