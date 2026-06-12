---
title: "Laptop- 2nd HD formatting"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by Uta on 2005-06-14
I recently installed Kubuntu on a Dell C800 laptop and I have ordered a 2nd HD that will go into the modular media bay (where the floppy drive was). Kubuntu is up and running perfectly so I just need some guidance as to what to do and in what order when I put an unformatted HD into the system. How do I find the drive (name) to format it and with what command (or app) do I format it with. All my other computers on my network are running Mac OS X so I will want this drive to be shared (eventually) on the network. Thanks in advance!

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=Uta]I recently installed Kubuntu on a Dell C800 laptop and I have ordered a 2nd HD that will go into the modular media bay (where the floppy drive was). Kubuntu is up and running perfectly so I just need some guidance as to what to do and in what order when I put an unformatted HD into the system. How do I find the drive (name) to format it and with what command (or app) do I format it with. All my other computers on my network are running Mac OS X so I will want this drive to be shared (eventually) on the network. Thanks in advance![/QUOTE]
 Try qtparted.

---

### Post by Uta on 2005-06-15
Ok, I installed this (QTParted) and when I tried to launch it I got this error message:
KDEInit could not launch '/usr/bin/gksudo'
Please explain what I should do now. Thank you--
-----------------------------------------------
OK I got the app. open with sudo but got a terminal message...
$ sudo qtparted
Error: Filesystem was not cleanly unmounted!  You should e2fsck.  Modifying an unclean filesystem could cause severe corruption.
----------------------------------------------
Is this because so far I only have one HD and it is busy (mounted)?
I just wanted to look at the GUI not modify my main HD.
Thanks--

---

