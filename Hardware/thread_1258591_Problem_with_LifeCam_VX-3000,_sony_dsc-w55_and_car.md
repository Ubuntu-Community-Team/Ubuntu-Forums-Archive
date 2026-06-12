---
title: "Problem with LifeCam VX-3000, sony dsc-w55 and cardreader."
date: 2009-09-05
forum: Hardware
---

### Post by fr0d0 on 2009-09-05
Good time!

I have laptop Acer 5220 (Intel Pentium Dual CPU T2310 @1.46GHz, DDR2-1Gb, 15,4", WGA, DVD-RW, card-reader SD-Multimediacard-memorystick duo pro-xD, WiFi, FireWire, DHCP), camera Sony Cybershot DSC-W55 7.2MPx and Microsoft LifeCam VX-3000.

Questions:
 - How could I use my card reder in Linux Mint 7/Ubuntu 9? I need to mount SD cards and Sony memory sticks.
 - How could I connect my camera to computer with cable? How can I mount it or what might I do?
 - How could I use my web cam?
So... The question is. How can I use this devices under Linux Mint 7/Ubuntu 9/Debian 5?

P.S.:
lsusb (when webcam is connected):
Bus 005 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.
lsusb (with camera):

Best regards,
Theodore Biryukov.

---

### Post by Liolikas on 2009-09-05
lsusb (with camera):
nothing?

lsusb (when webcam is connected):
Bus 005 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.
Maybe ask microsoft for Linux drivers? :popcorn:
Or just use forum search button with model?
[http://ubuntuforums.org/showthread.php?t=381188](http://ubuntuforums.org/showthread.php?t=381188)

Show **ls /dev/sd*** too.

---

### Post by fr0d0 on 2009-09-05
ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sda5

But now webcam isn't connected. If you need this command with webcam then I'll post it later.

---

### Post by fr0d0 on 2009-09-05
with webcam it's same

---

### Post by fr0d0 on 2009-09-05
Oh! Also! About the cam. As I can judge gspca driver support it. And now I'm trying to install it. What about the others?

---

### Post by fr0d0 on 2009-09-06
I can't install gspca. It faults with errors.

home@localhost ~/gspcav1-20071224 $ sudo ./gspca_build 
[sudo] password for home: 
 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

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
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/home/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/home/gspcav1-20071224/gspca_core.o
/home/home/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/home/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/home/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/home/gspcav1-20071224/gspca_core.c: At top level:
/home/home/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/home/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/home/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/home/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/home/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/home/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/home/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/home/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/home/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/home/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

Best regards,
Theodore Biryukov.

---

### Post by Vevmesteren on 2009-09-27
Any news in regards to this? I am stuck with this MS camera as well...

---

### Post by fr0d0 on 2009-09-28
Yes. Yes. You are a brick. I forgot about this topic because no one answer.

I've solved problem with my LifeCam: [http://ubuntuforums.org/showthread.php?t=1034988](http://ubuntuforums.org/showthread.php?t=1034988) :P
CardReader also works properly but only with SD-cards.

So. Maybe you know, how to use my photo-camera sony dsc-w55 or how to use Memory Stick Pro Duo with my card-reader?

Best regards,
Theodore Biryukov.
:popcorn:

---

### Post by fr0d0 on 2010-06-21
People, does anybody know how to use [   0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)   ] under linux.
Usual sd card is working, but I have sony memory stick (pro duo). And it's really painful for me to get no support of this device.

About LifeCam (VX-3000): Yes, IT starts to WORK if you apply what I've written in previous posts, BUT IT DOES NOT WORK WITH SKYPE. And it is painful for me because no one uses free variants (Ekiga etc.).

I hope it will be solved.
Thanks.
Fedor Biryukov.


[RIGHT] Hack the planet![/RIGHT]

---

### Post by fr0d0 on 2010-06-21
Is this a solution of this problem? 
> Enable USB Mass Storage support and SCSI generic support
[LEFT][http://www.darkridge.com/~jpr5/r505jl/]("http://www.darkridge.com/%7Ejpr5/r505jl/")
[/LEFT]

---

### Post by fr0d0 on 2012-07-13
In Ubuntu 11.10 and newer LifeCam works out of the box!

---

### Post by overdrank on 2012-07-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

