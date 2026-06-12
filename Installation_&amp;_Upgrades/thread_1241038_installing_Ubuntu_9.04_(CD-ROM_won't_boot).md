---
title: "installing Ubuntu 9.04 (CD-ROM won't boot)"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by peter_kint on 2009-08-15
Hi,
As a Windows Vista user, I am an absolute newbie here.
I bought LINUX FORMAT Special Edition with DVD (Ubuntu 9.04).
I wanted to boot from the DVD, and went -as the booklet said- into the **BIOS Setup**, to change the boot order (I chose the CD-ROM as 1 , HD as 2).
**My PC refuses to boot from the LINUX DVD.**

Any suggestions?
Thx,
peter

---

### Post by running_rabbit07 on 2009-08-15
Have you hit the key that takes you to the actual boot menu? Not the one that goes to bios. 

I have never heard about the install disk you are using but if it has Ubuntu 9.04 on it, it should work. 

Let us know what's happening.

Edit: Do you get the install menu when you load the CD while your system is running? I have installed this way before.

---

### Post by peter_kint on 2009-08-15
> **running_rabbit07 said:**
> Have you hit the key that takes you to the actual boot menu? Not the one that goes to bios. 

I have never heard about the install disk you are using but if it has Ubuntu 9.04 on it, it should work. 

Let us know what's happening.

Edit: Do you get the install menu when you load the CD while your system is running? I have installed this way before.

Thx for the reply rabbit.
I always assumed automatically that I was in the boot menu, without looking any further. 
thx to your suggestion i found the **real boot menu**.  
It works!
Thx again,
peter

---

### Post by raymondh on 2009-08-15
Peter,

I, likewise, have not tried the DVD's offered by the magazine.

As an alternative, you could (from windows) download and burn your own liveCD.  Cost for you will be a blank cd-r and your time.  Benefit will be the learning experience.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Some tips:

-  Read the release notes.  Here's [Jaunty]("http://www.ubuntu.com/getubuntu/releasenotes/904"), as an example.  It may read daunting/confusing but it'll give you a clue.
-  Use a burning software that will allow you to burn the iso. image slow, as slow as possible.  Most modern burning softwares' are good enough even burning fast .... but, it is still recommended to burn the image slow to minimize writing errors.  In windows, i use [cdburnerxp]("http://cdburnerxp.se/"), a free tool.
-  When you boot into the liveCD, one of the initial options is to check the cd for defects.  Try it.
-  If you decide to verify md5, here's a [how to]("https://help.ubuntu.com/community/HowToMD5SUM").
-  If satisfied, another initial option is to go live session (TRY UBUNTU WITHOUT ANY CHANGES).  Try it and see how the version reacts well to your system and hardware.

Some pre-installation decisions.

-  You may decide to do a [wubi-install]("https://wiki.ubuntu.com/WubiGuide").  Do read up on its' pros and cons.
-  You may decide to install Ubuntu in it's own partition.  Here are some links for reference:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

A [popular reference material]("http://www.ubuntupocketguide.com/download_main.html") which also has an installation guide.

Whatever you choose to do (use the DVD, burn your own liveCD, wubi, partitioned, etc) .... back-up your files first.  Then, defrag windows as a fragmented HD may cause you problems later on.  

If you decide to shrink Vista to create a partition for Ubuntu, use Vista's disk management tool to shrink a Vista/windows partition.  If you decide to use the built-in installer in the liveDVD or liveCD, you will have the option to install side-by-side (or guided resize).  Remember to grab the slider to allocate preferred sizings for both Vista and Ubuntu.  Otherwise, you will end up with a 2.5GB-sized install which is not enough for the first update.

Have fun.  Back-up.  Familiarize yourself with the process. Good luck and Happy Ubuntu-ing.

---

