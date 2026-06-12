---
title: "Unable to upgrade to/install Feisty after XP removal"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by optimarcus_prime on 2007-05-06
About 4 days ago I tried to install XP on my Dell Inspiron E1505 after having Ubuntu installed for quite some time.  However, I couldn't get it to work properly for different problems, so I uninstalled almost immediately after installing.  That's where the problems began.  After uninstalling, Feisty gave me the error message that I will describe below.

I have a backup of my Feisty stored on an external hard drive, made using the method described [here]("http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup+restore"), so I tried to reinstall a fresh version of Ubuntu so that I could restore, but ran into problems.  I have gone about this several different ways:

1. Using a Feisty install disk to reinstall Ubuntu, but got this error message when attempting to load CD, after the loading screen:
> Failed to set up the X server (Your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?  Y/N

Upon choosing Y I get:
> X Window System version 7.2.0
Release date: 22 January 2007
X protocol version 11, Revision 0, Release 7.2
Build Operating system: Linux Ubuntu
Current Operating system: Linux Ubuntu 2.0-20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i696
Build Date : 04 April 2007
     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
     to make sure you have the latest version.
Module loader present.
Markers: (...)(==) Default settings(...)
(==) Log File: "/var/log/Xorg.0.log," Time: Sun May 6 20:18:48 2007
(==) Using config file: "/etc/X11/xorg.conf"

After choosing OK, get the following message:
> Would you like to see the detailed X server output as well?

Choose OK again, and get the same message as above.

Then after one more OK, get this message:
> The X server is now disabled.  Restart GDM when it is configured correctly

Then after OK the screen moves back to the list of process that are being run at startup, and it frozen.


2.  If I try to install with an Edgy install disk, it works fine.  However, when I get to a working Edgy, and try to either upgrade to Feisty or restore using my backup file, I get the same error message as above after the process is completed.


Any thoughts?  I've currently got a working version of Edgy running, just so that I can get online and post this, etc.  Thanks!

---

### Post by jbmech006 on 2007-05-06
Your not only one with Feisty problems. I have been looking for a solution to this all day and have not found one. After trying a bunch of different suggestions that didn't work I am going to try the alternative install located on the Ubuntu install page. Hopefully the alternative install wont have the same problems as the desktop install.

---

### Post by optimarcus_prime on 2007-05-06
Not a bad idea.  Let me know if that works, please

---

### Post by optimarcus_prime on 2007-05-07
Would it be best for me to just start over sticking to Edgy?  I was liking Feisty so far, but if it will not run, then I have no choice.

Also, if I decide to stay with Edgy, will the files that I have stored on the backup still work, even though the operating system version has been downgraded?  Thanks.

---

### Post by optimarcus_prime on 2007-05-07
I know I'm being annoying, but it's finals time and I really need a working laptop.  Does anyone know how to resolve this issue?  I'm desperate.

---

### Post by optimarcus_prime on 2007-05-07
Resolved!

Found this thread, explains everything very nicely!

[http://ubuntuforums.org/showthread.php?t=399913&highlight=how+to+feisty+beryl+on+dell+inspiron](http://ubuntuforums.org/showthread.php?t=399913&highlight=how+to+feisty+beryl+on+dell+inspiron)

---

