---
title: "Problems getting Syntek Webcam to work"
date: 2009-06-08
forum: Hardware
---

### Post by The Judderman on 2009-06-08
Dear All,

I have an Asus laptop with a syntek webcam integrated. I've tried to follow these instructions ([http://doc.ubuntu-fr.org/syntek]("http://doc.ubuntu-fr.org/syntek")) but get an error on making the driver file. Can anybody help? 

lsusb gives me this:

> peter@Ubuntu:~$ lsusb
Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The guide gives 2 ways of installing the driver, with a tar and with svn. I've tried both, and when it comes to making the file this is what happens!

> peter@Ubuntu:~$ cd ./syntek
peter@Ubuntu:~/syntek$ svn co [https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver)
A    driver/Kconfig
A    driver/stk11xx-dev.c
A    driver/stk11xx-dev-a311.c
A    driver/stk11xx-dev.h
A    driver/stk11xx-dev-6a31.c
A    driver/stk11xx-dev-a821.c
A    driver/stk11xx-dev-6a33.c
A    driver/stk11xx-dev-6a51.c
A    driver/stk11xx-usb.c
A    driver/README
A    driver/stk11xx-dev-6a54.c
A    driver/stk11xx-dev-6d51.c
A    driver/stk11xx.txt
A    driver/Makefile.standalone
A    driver/stk11xx-bayer.c
A    driver/stk11xx-v4l.c
A    driver/stk11xx-sysfs.c
A    driver/stk11xx.h
A    driver/Kbuild
A    driver/doxygen.cfg
A    driver/Makefile
A    driver/stk11xx-buf.c
Checked out revision 87.
peter@Ubuntu:~/syntek$ cd driver
peter@Ubuntu:~/syntek/driver$ ls
doxygen.cfg          stk11xx-bayer.c     stk11xx-dev-6d51.c  stk11xx-sysfs.c
Kbuild               stk11xx-buf.c       stk11xx-dev-a311.c  stk11xx.txt
Kconfig              stk11xx-dev-6a31.c  stk11xx-dev-a821.c  stk11xx-usb.c
Makefile             stk11xx-dev-6a33.c  stk11xx-dev.c       stk11xx-v4l.c
Makefile.standalone  stk11xx-dev-6a51.c  stk11xx-dev.h
README               stk11xx-dev-6a54.c  stk11xx.h
peter@Ubuntu:~/syntek/driver$ make -f Makefile
make: *** No targets. Stop.
peter@Ubuntu:~/syntek/driver$ make -f Makefile.standalone 
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/peter/syntek/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/peter/syntek/driver/stk11xx-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/peter/syntek/driver/stk11xx-usb.c:34:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:256:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/peter/syntek/driver/stk11xx-usb.c:34:
include/linux/mmzone.h:277: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from /home/peter/syntek/driver/stk11xx-usb.c:41:
include/linux/mm.h:437:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:485:62: warning: "NR_PAGEFLAGS" is not defined
make[2]: *** [/home/peter/syntek/driver/stk11xx-usb.o] Error 1
make[1]: *** [_module_/home/peter/syntek/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [driver] Error 2
peter@Ubuntu:~/syntek/driver$ 

if anyone can help, I'd be very happy!!! It is the only thing that I'm going back to Windoze for at the moment, to communicate with family overseas!

I've tried easycam and that doesn't pick up anything either...

Thoughts?

Thanks,

The Judderman

---

### Post by The Judderman on 2009-06-10
bump

---

### Post by rastaxe on 2009-06-18
Hi, I tried the version 1.4 of the stk11xx driver that compile with no errors. But for me, that driver didn't work.
I followed this post and now my syntek cam works:
[http://ubuntuforums.org/showthread.php?t=935072]("http://ubuntuforums.org/showthread.php?t=935072")

I simply tried this:
  rmmod uvcvideo
  modprobe uvcvideo quirks=16
and now the cam works with cheese and skype!

---

### Post by The Judderman on 2009-06-19
thanks for getting back to me, but I still can't get it to work. Do you need to "sudo modprobe" or just modprobe?

With cheese it telles me that there is no webcam on /dev/video and skype says no webcam detected!

Not sure what to do... 

Thanks for getting back to me though!

---

### Post by The Judderman on 2009-07-09
bump?!?

---

### Post by noobi_agocs on 2009-07-09
Hi there!


I had also problems whit my webcam. I googled around the web every evening after work to solve the problem. FINALLY it works for me...


I have an ASUS F5VL series laptop, and i'm using Ubuntu 9.04

1.
So, maybe the most important thing is, that you need to download the stk11xx Syntek driver, **BUT the 1.4.0 release**! This is very important! I had no chance to install the 2.0.0 release...

Here you can download it: [http://sourceforge.net/projects/syntekdriver/](http://sourceforge.net/projects/syntekdriver/)

2.
Then, I followed this HOWTO: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

This is a french HOWTO (i dont speak french), but it's excellent. I followed it step by step, EXCEPT that I didn't donwloaded the latest syntek driver using the svn command.

Later I found an english HOWTO: [http://www.zer0.net/2007/12/asus-syn...lation-on.html](http://www.zer0.net/2007/12/asus-syn...lation-on.html)

3.
After this i installed video4linux using the command:
$ sudo apt-get install v4l-conf

4.
The last step was to add my user nick to a group that is allowed to use the webcam. The command is:
$ sudo adduser USERNICK video

Then RESTART...


After this i've tried the webcam whit: Camorama, aMSN and Skype. All of them recognized whitout any problem the webcam.


I hope this helps you a little...
Have a nice day! Cheers!

noobi

----------------------------------------------------
ASUS F5VL Series Laptop, Intel Core2Duo T5250, ATI X2300, using Ubuntu 9.04

---

### Post by The Judderman on 2009-07-10
Thank you soooooo much!!!!

I've been trying to work it out for soooo long! and it works!!! It is obviously something to do with the later versions of the driver. Why on earth does it work with the old versions and not the new ones? that seems ridiculous to me!

Thanks for sharing this with me.

This has solved my problem. The webcam is now working on skype and aMSN (though not found in cheese, but that doesn't matter!)

Thanks again noobi

---

### Post by Kaisersoze on 2009-08-15
> **noobi_agocs said:**
> Hi there!


I had also problems whit my webcam. I googled around the web every evening after work to solve the problem. FINALLY it works for me...


I have an ASUS F5VL series laptop, and i'm using Ubuntu 9.04

1.
So, maybe the most important thing is, that you need to download the stk11xx Syntek driver, **BUT the 1.4.0 release**! This is very important! I had no chance to install the 2.0.0 release...

Here you can download it: [http://sourceforge.net/projects/syntekdriver/](http://sourceforge.net/projects/syntekdriver/)

2.
Then, I followed this HOWTO: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

This is a french HOWTO (i dont speak french), but it's excellent. I followed it step by step, EXCEPT that I didn't donwloaded the latest syntek driver using the svn command.

Later I found an english HOWTO: [http://www.zer0.net/2007/12/asus-syn...lation-on.html](http://www.zer0.net/2007/12/asus-syn...lation-on.html)

3.
After this i installed video4linux using the command:
$ sudo apt-get install v4l-conf

4.
The last step was to add my user nick to a group that is allowed to use the webcam. The command is:
$ sudo adduser USERNICK video

Then RESTART...


After this i've tried the webcam whit: Camorama, aMSN and Skype. All of them recognized whitout any problem the webcam.


I hope this helps you a little...
Have a nice day! Cheers!

noobi

----------------------------------------------------
ASUS F5VL Series Laptop, Intel Core2Duo T5250, ATI X2300, using Ubuntu 9.04

Kudos to you noobi! It worked! I have pasted this solution on the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123)

I gave credit to you!

Many Kudos!

Cheers :guitar:

---

### Post by HAG1976 on 2009-08-29
It is possible to compile the latest syntek driver v.2.0 from svn. I am using kubuntu 9.04 with kernel 2.6.30 /from xorg-edgers repository/. My laptop is Asus F5RL,camera id 174f:6a31. I had to make changes to stk11xx-v4l.c commenting the following lines /found this solution on syntek sourceforge forum/
was:
#ifdef CONFIG_COMPAT  
.compat_ioctl = v4l2_compat_ioctl32,  
#endif 

became:
//#ifdef CONFIG_COMPAT  
//.compat_ioctl = v4l2_compat_ioctl32,  
//#endif 

Driver compiles without errors. Next add the user's group to video in file /etc/group, to be able to access /dev/video0 as user /works with wxcam/

---

### Post by The Judderman on 2009-10-23
Just for completeness, I didn't manage to compile the 2.0 module by editing the stk11xx-v4l.c file as HAG1976 suggested. Not sure why! The syntax wasn't the same as was he had.

However, I did manage to compile it by copying that file from the 1.4 version (see above) into the new directory and then it compiled perfectly.

How do I report this to launchpad?

Cheers,

The Judderman

---

