---
title: "unreal tornament 2004"
date: 2005-11-16
forum: General Help
---

### Post by trandojedi on 2005-11-16
hi... i dled umm ut, it was the deviance dvd. it has a linux installer. the problem is ubuntu won't let me run the .sh. even with sudo.

i think this is the main lin ut disc out there so if someone has installed it pls help

cheers

---

### Post by kruz on 2005-11-16
rename the script without the .sh

and then

sudo ./script

see if that works

---

### Post by Kyral on 2005-11-16
Linux will still know its a script

You don't even need to be root to run it. No offense kruz but your method doesn't hold water.

OP can I see the output when you try to do it?

---

### Post by trandojedi on 2005-11-16
i'm @ uni atm... wen i get home i will post the infos... it said something about insufficient privileges. soz

---

### Post by drummer on 2005-11-17
maybe the .sh isn't executable? "chmod +x script.sh"
Or maybe needs to run as root (it installed into /opt when I installed the UT2004 demo).

---

### Post by trandojedi on 2005-11-17
here's wat happens

paskog01@ubuntu:~$ cd /media/
paskog01@ubuntu:/media$ ls
cdrom  cdrom0  cdrom1  floppy  floppy0
paskog01@ubuntu:/media$ cd cdrom0/
paskog01@ubuntu:/media/cdrom0$ ls
AutoRun.inf  CD2  CD4  CD6       linux-installer.sh
CD1          CD3  CD5  DEViANCE  Setup.exe
paskog01@ubuntu:/media/cdrom0$ ./linux-installer
bash: ./linux-installer: No such file or directory
paskog01@ubuntu:/media/cdrom0$ ./linux-installer.sh
bash: ./linux-installer.sh: /bin/sh: bad interpreter: Permission denied
paskog01@ubuntu:/media/cdrom0$
paskog01@ubuntu:/media/cdrom0$ sudo ./linux-installer.sh
Password:
sudo: unable to execute ./linux-installer.sh: Permission denied
paskog01@ubuntu:/media/cdrom0$

---

### Post by the_it on 2005-11-17
```
paskog01@ubuntu:/media/cdrom0$ ls
AutoRun.inf CD2 CD4 CD6 linux-installer.sh
CD1 CD3 CD5 DEViANCE Setup.exe
paskog01@ubuntu:/media/cdrom0$ ./linux-installer
bash: ./linux-installer: No such file or directory
paskog01@ubuntu:/media/cdrom0$ ./linux-installer.sh
bash: ./linux-installer.sh: /bin/sh: bad interpreter: Permission denied
paskog01@ubuntu:/media/cdrom0$
paskog01@ubuntu:/media/cdrom0$ sudo ./linux-installer.sh
Password:
sudo: unable to execute ./linux-installer.sh: Permission denied
paskog01@ubuntu:/media/cdrom0$
```
I'm suspecting it doesn't recognize the script as an executable.  Now, to run it directly from the cd, you simply use the sh command.
```
usage: sh *scriptname.sh*
```
you can also use bash, it has the same usage
```
usage: bash *scriptname.sh*
```
these two are equivalent to typing
```
./scriptname.sh
```
if the script is executable.  However, executable files are identified by the executable permission bit in the filesystem: your CDROM likely does not have that on your file.  The quick way to get around it is to either
1) declare it as executable OR
2) run it with sh (or bash)

so
```
paskog01@ubuntu:/media/cdrom0$ sudo sh installer.sh
```
should work.

Hope it works for you.

---

