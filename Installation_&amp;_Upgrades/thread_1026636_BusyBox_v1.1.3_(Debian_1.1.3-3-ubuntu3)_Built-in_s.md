---
title: "BusyBox v1.1.3 (Debian 1:.1.3-3-ubuntu3) Built-in shell (ash) Enter 'help' for a list"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by miros84 on 2008-12-31
Hi. I have installed ubuntu in several computars, and everything went good. I tried to insall it on my wife´s computar, it´s Sony Vaio but I have this problem: "BusyBox v1.1.3 (Debian 1:.1.3-3-ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands."
I recive this error when I try to load the live CD Ubuntu 8.10 after choosing the language. I looked in internet, but I couldnot fix my problem. I tried to change
"quiet splash"
with
"all_generic_ide"
in options entering with F6 but was the same. I couldnot load Live cd ubuntu 8.10
Please help me.

---

### Post by dstew on 2008-12-31
Are you sure the CD is OK? Does the same CD boot and install in other computers?

---

### Post by clattems on 2008-12-31
> **miros84 said:**
> Hi. I have installed ubuntu in several computars, and everything went good. I tried to insall it on my wife´s computar, it´s Sony Vaio but I have this problem: "BusyBox v1.1.3 (Debian 1:.1.3-3-ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands."
I recive this error when I try to load the live CD Ubuntu 8.10 after choosing the language. I looked in internet, but I couldnot fix my problem. I tried to change
"quiet splash"
with
"all_generic_ide"
in options entering with F6 but was the same. I couldnot load Live cd ubuntu 8.10
Please help me.

I'm having the the same issue.  I installed it on an older Dell Laptop and it installed fine.  When I tried to install it on my box I use at home, I got the same error.  I've read around that typing 'exit' after a couple minutes works for some people.  I've also read that changing the ROOTDELAY=' ' to 90 works.  I'm going to try that when I get back home.  Let me know if it works for you.

---

### Post by clattems on 2009-01-02
Adding rootdelay did not work for me.  The only way I was able to reload Ubuntu was to put my Vista disk in, start the installation, delete the partition I created with Ubuntu, back out of the installation, and then finally reload Ubuntu.  It worked all day yesterday, and then I woke up this morning, booted, and I was back to the BusyBox screen.  Any suggestions?

---

### Post by miros84 on 2009-01-02
> **dstew said:**
> Are you sure the CD is OK? Does the same CD boot and install in other computers?

Yes. I´m sure that the dvd is OK. I have 2 dvd with ubuntu 8.10
I used the same dvd to installed it on another computers. I also tried to install Sidux, just to see what happens, and I had exactly the same problem. "BusyBox v1.1.3 (Debian 1:.1.3-3-ubuntu3) Built-in shell (ash) Enter 'help' for a list"
What can I try?

---

### Post by dstew on 2009-01-02
For some reason, the kernel on the CD was not able to run on your system. Sometimes you can tell why by looking at the error messages that are produced during the boot attempt. Modify the kernel line so that "quiet splash" is changed to "nosplash". In other words, remove "quiet" and change "splash" to "nosplash". Look at the kernel messages to see what errors are coming up.

I think there is also a log file kept in the union file system (the file system in RAM) that the live CD uses. The logs would be in the /var/log directory. If you can get there using BusyBox, maybe you can see the errors.

Another thing to try is the Alternate Install CD. It installs the same Ubuntu desktop using a text-based interface that sometimes works better than the Live CD.

---

### Post by miros84 on 2009-01-05
> **dstew said:**
> For some reason, the kernel on the CD was not able to run on your system. Sometimes you can tell why by looking at the error messages that are produced during the boot attempt. Modify the kernel line so that "quiet splash" is changed to "nosplash". In other words, remove "quiet" and change "splash" to "nosplash". Look at the kernel messages to see what errors are coming up.

I think there is also a log file kept in the union file system (the file system in RAM) that the live CD uses. The logs would be in the /var/log directory. If you can get there using BusyBox, maybe you can see the errors.

Another thing to try is the Alternate Install CD. It installs the same Ubuntu desktop using a text-based interface that sometimes works better than the Live CD.

Hi again. I changed "quite splash" to "nosplash" but no results. Also I try to get to log directori, but I don´t know how to get. Where can I download the Alternate Install CD. I know that it´s on ubuntu.com, but how can I make the diferent between the standart version and the alternative version. I looked for errors in the BusyBox but wasnot errors. Any suggestions?

---

### Post by miros84 on 2009-01-05
> **clattems said:**
> I'm having the the same issue.  I installed it on an older Dell Laptop and it installed fine.  When I tried to install it on my box I use at home, I got the same error.  I've read around that typing 'exit' after a couple minutes works for some people.  I've also read that changing the ROOTDELAY=' ' to 90 works.  I'm going to try that when I get back home.  Let me know if it works for you.

I looked for ROOTDELAY to change it, but I cannot find it. Where did you  changed that? In F6 options. I have not this option there. I also typed exit in a couple of minutes but that doesnot work.

---

### Post by dstew on 2009-01-05
> Where can I download the Alternate Install CD.Here is the [Alternate Installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") page.

---

