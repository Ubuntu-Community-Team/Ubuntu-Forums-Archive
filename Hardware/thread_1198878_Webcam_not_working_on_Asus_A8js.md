---
title: "Webcam not working on Asus A8js"
date: 2009-06-28
forum: Hardware
---

### Post by PreciousBodilyFluids on 2009-06-28
Hello -

I'm very new to Ubuntu - just installed yesterday, still getting used to it, but I like it.

My laptop is an Asus A8js, and the one piece of hardware I've tried so far that hasn't worked is my webcam. There's a bug report on the issue here, with a picture that looks like mine:

[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/281437](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/281437)

So, after searching some more I found several links to the following page:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Apparently, many others have gotten their webcams working using the drivers from that link. I also found some short instructions:

[http://ubuntuforums.org/showthread.php?p=2126584#post2126584](http://ubuntuforums.org/showthread.php?p=2126584#post2126584)

So, I followed them, and did:

sudo apt-get install build-essential
(went into the directory of the downloaded and extracted drivers)
make

And I got the following output:

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/chris/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/chris/gspcav1-20071224/gspca_core.o
/home/chris/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/chris/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/chris/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/chris/gspcav1-20071224/gspca_core.c: At top level:
/home/chris/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/chris/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/chris/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/chris/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/chris/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/chris/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/chris/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/chris/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/chris/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/chris/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

That said, I also found a description of what to do to fix a similar error here:

[http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html)
(about one-third of the way down, under "webcam")

The error message looks similar, but not identical. It suggests editing the gspca_core.c file at the area mentioned in the error message, but things are different in my error message, and I'm not sure what to do.

That's all I know, sorry if it's too much or too confusing.

Thanks in advance!

---

### Post by PreciousBodilyFluids on 2009-06-28
Nobody has any ideas?

---

### Post by PreciousBodilyFluids on 2009-06-30
Well, I found the following post:

[http://ubuntuforums.org/showpost.php?p=6402989&postcount=14](http://ubuntuforums.org/showpost.php?p=6402989&postcount=14)

I was able to apply the patch properly, and things seemed to go well when I built it - I didn't copy down the output, but there were no obvious error messages.

So I rebooted my computer (not sure if that was necessary, but I'm just coming off windows - force of habit), loaded up skype, and now my webcam just isn't detected at all.

I'm really not sure where to even begin diagnosing this - any suggestions?

Thanks

---

### Post by PreciousBodilyFluids on 2009-07-06
Well, I'm not sure what changed, but it's back to the broken-up image of before. I tried patching and installing the drivers again, and copied the output this time:

chris@chris-laptop:~/Desktop/gspcav1-20071224$ sudo ./gspca_build
[sudo] password for chris: 

 REMOVE the old module if present

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/chris/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/chris/Desktop/gspcav1-20071224/gspca_core.o
  CC [M]  /home/chris/Desktop/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /home/chris/Desktop/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chris/Desktop/gspcav1-20071224/gspca.mod.o
  LD [M]  /home/chris/Desktop/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
chris@chris-laptop:~/Desktop/gspcav1-20071224$ 



It made no difference. Does anyone have any suggestions? At all? No matter how unlikely? I'm at the end of my rope. I'm considering buying a new webcam, but with all the people on this forum having problems with webcams on Ubuntu and not getting help, I'm not sure there's any point.

Thanks to anyone who can help.

---

### Post by noobi_agocs on 2009-07-08
Hello!


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
ASUS F5VL Series, Intel Core2Duo T5250, ATI X2300

---

### Post by PreciousBodilyFluids on 2009-07-08
Hi -

Thanks so much for the reply.

When I ran lsusb under the terminal, I saw the following:

chris@chris-laptop:~$ lsusb
Bus 001 Device 004: ID 0ac8:0321 Z-Star Microelectronics Corp. USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


The [English howto]("http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html") you mentioned said to look for a device starting with 05e1 or 174f, which doesn't match my webcam above. I'm not sure what to do with it.

Also, I've attached a picture of Skype, showing what my webcam is displaying, so that people can see the image distortion that I'm talking about.

Thanks so much for your advice, noobi_agocs, I really appreciate it!

---

### Post by noobi_agocs on 2009-07-09
Hello,


now I see that you have another type of webcam. The English and French HOWTO´s are written especially for the Syntek Webcam (built-in webcams for ASUS).

The lsusb command shows the exact name/type of USB devices currently plugged in. We should find the proper driver for Z-Star Microelectronics Corp. USB 2.0 Webcam.

I´ll try to search around the web...
But now, I have to work... :) Today evening I´ll find some time to search for any HOWTO´s or drivers (19:00 GMT).


Aloha!

----------------------------------------------------
ASUS F5VL Series Laptop, Intel Core2Duo T5250, ATI X2300, using Ubuntu 9.04

---

### Post by noobi_agocs on 2009-07-12
Hello,


sorry for the latency, but I was little bit busy in the last days...
So I was thinking a little bit. Try the command "dmesg". This will print the attached hardwares. Find your webcam and look for possible errors. Maybe this helps something...

My output is the following:


[   12.326839] stk11xx: Syntek USB2.0 webcam driver startup
[   12.326873] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[   12.326875] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A31.
[   12.326879] stk11xx: Release: 0005
[   12.326882] stk11xx: Number of interfaces : 1
[   12.327718] stk11xx: Initialize USB2.0 Syntek Camera
[   12.450471] stk11xx: Check device return error (0x0201 = 0C) !
[   12.462133] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   12.506437] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   12.525721] stk11xx: Syntek USB2.0 Camera is ready
[   12.525832] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[   12.525875] usbcore: registered new interface driver usb_stk11xx_driver
[   12.525906] stk11xx: v1.3.1 : Syntek USB Video Camera


Since you already installed the webcam driver and the system recognizes it "only" the picture distortion is still there, I would advice to install video4linux. Maybe this can help...

I also found a similar bug description here: [https://bugs.launchpad.net/bugs/293259](https://bugs.launchpad.net/bugs/293259)


Cheers!

---

