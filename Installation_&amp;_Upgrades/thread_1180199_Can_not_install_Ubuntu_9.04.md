---
title: "Can not install Ubuntu 9.04"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by Mimir09 on 2009-06-06
Hi everyone, I am new to Ubuntu (or for that mater linux in general) and I am trying to install Ubuntu 9.04.  When I try to either use the LiveCD or install it, I will get a loading screen and then after a bit I get the following:

> Loading, please wait...
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686

The programs included with the Ubuntu system are free software:
the exact distrubtion terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$

I can not get to the desktop or installer.  I have an off brand laptop that I am wanting to dual boot from.  I have already tried the disk on my desktop and it worked flawlessly.  I am guessing it has something to do with my graphics card.

If someone could explain what is happening and how to fix it or point me to a thread that already contains it I would appreciate it.

---

### Post by matamoscas on 2009-06-06
I must say, I am no expert, so I hesitate to give any advice at all...but...here goes.

Yeah, I think it is a video problem.  When I have booted to a command prompt in the past, it was because my xorg.conf was not properly configurated.

I don't think a video card would out-and-out NOT work, so I think it just needs to be configured.

Try something like X -configure at the command prompt, but that might only work ONCE it is installed.

Anyway, that is the best I can do...

Good luck.

---

### Post by merlinus on 2009-06-06
You might try reburning the .iso at a slow (4x) or less speed.  Also, do a checksum:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And you also might post system specs.

---

### Post by Mimir09 on 2009-06-06
Thanks for getting back so quick.  I have check the ISO file and it is correct.  I also tried the following commands:

x -configure
x -config
sudo -configure
sudo -config
xorg.config
sudo xorg
sudo scorg.config

and really a bunch of other ones that wouldn't give me anything but a message saying it is not a valid command.

The system specs are as follows:
Averatec 3200 Series 
XP SP3
AMD Athlon XP-M
256 Ram
40 GB HD with 30 GB free
VIA/S3G UniChrome Graphics

If you need any more information let me know

Thanks for the help

---

### Post by merlinus on 2009-06-06
It is recommended to have at least 384M RAM for ubuntu, so you might try xubuntu.

But something is amiss if you are being dumped to a CLI and not getting to a menu if booting from the burned .iso.

Also, you did burn the .iso as a disk image?

---

### Post by Mimir09 on 2009-06-06
I should have mentioned that I have also tried v. 8.04 and xubuntu (All verified with the Md5 hash and did the 'check CD for defects')and they all get me to the same place.  So it is something fundamental to my system.  But I will switch over to xubuntu due to the memory considerations.

I did burn it as an image as well

---

### Post by matamoscas on 2009-06-06
My experience with older versions has not been as good.  But, the hardware you are mentioning, makes me think that you might have MORE luck by trying older versions, even as far back as *GULP* 6.0. 

My hardware, as I type, is not the most recent, so I have been using 8.04.
In other words, 9.0 did not work so sweet for me =( regrettably.

As I have promised this hardware away -- as I am planning to buy new hardware, I will go with 9.  *yippie!*

Anyway, my point is, you need to also be mindful to match the hardware with the software.

With your specs, I probably would try to install 6, and see how that goes.

---

### Post by presence1960 on 2009-06-06
anything prior to Hardy 8.04 is no longer supported. Why don't you try the alternate text based installer. Download it here : [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

see this also : [https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html)

you should be able to install with the alternate text based installer.

---

### Post by Mimir09 on 2009-06-06
I was able to get the OS installed using the alternate CD (Not dual boot, which is ok)  However when it starts it still brings me to the same screen.  I think i'm suppose to edit my graphics settings using xorg, but I can't find this file let alone edit it.

Thanks for the help getting it installed though

---

### Post by presence1960 on 2009-06-07
> **Mimir09 said:**
> I was able to get the OS installed using the alternate CD (Not dual boot, which is ok)  However when it starts it still brings me to the same screen.  I think i'm suppose to edit my graphics settings using xorg, but I can't find this file let alone edit it.

Thanks for the help getting it installed though

This is a long shot but when you boot, select recovery mode. when the menu comes up look for fix graphics or something similar. Choose that option then reboot normally.

---

### Post by Mimir09 on 2009-06-07
I rebooted and tried:

xfix    Try to auto repair graphic problems

It didn't work

---

### Post by Mimir09 on 2009-06-08
I found a solution to the problem:

[http://ubuntuforums.org/showthread.php?t=930121](http://ubuntuforums.org/showthread.php?t=930121)

thanks to everyone for their help

---

