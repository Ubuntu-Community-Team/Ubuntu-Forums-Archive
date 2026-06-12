---
title: "brother printer and a noob needs help"
date: 2008-09-02
forum: Hardware
---

### Post by dhinderliter on 2008-09-02
i tried following the directions on the brother site...i really did. after typeing the first command it tells me that it requires read/write access...i haven't a clue what to do.

i have a brother MFC-240c printer that i love. It DOES install with "text-only" printing or whatever but it then says not supported or something when i try to print. i downloaded the debian versions and they "installed" or whatever but it didn't change the text only printing.

i'm completely lost. i am running 8.04 and have only used it for 2 days!

---

### Post by ajgreeny on 2008-09-02
It is possible that the instruction on the brother site are for other distros which use a root login account.  That is disabled in ubuntu but you may be able to get the thing to work properly by either using "sudo" in front of the commands, or if it uses a gnome application to carry out the installation of the printer, open that application with ```
gksu appname
```and continue from there.

---

### Post by dhinderliter on 2008-09-02
heres what i get when i try sudo

danielle@danielle-laptop:~$ sudo dpkg -i --force-all --force-architecture mfc240clpr-1.0.1-1.i386.deb
dpkg: error processing mfc240clpr-1.0.1-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc240clpr-1.0.1-1.i386.deb
danielle@danielle-laptop:~$ 

when i used gksu "appname" it gave me a weird list of things i could do but nothing about a printer.

i can see the drivers are saved on my desktp. i tried useing the entire file location/name. i just don't understand alot of this stuff in the first place

---

### Post by ajgreeny on 2008-09-03
The error shows that either you got the name wrong or you were not in the correct location.  I don't know where the file you are trying to install is located, but if it is on your desktop you will need to change directory to that before the command you used will work.  Try ```
cd Desktop && sudo dpkg -i --force-all --force-architecture mfc240clpr-1.0.1-1.i386.deb
```Just make sure you have the filename exactly right, including all the . - and cases, to make sure there is a chance.

---

