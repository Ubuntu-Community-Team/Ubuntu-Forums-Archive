---
title: "promise raid driver problems"
date: 2009-05-04
forum: Hardware
---

### Post by LashSilence83 on 2009-05-04
I have an MSI K9A2 Platinum mobo which has 6 total sata ports, 2 of which are controlled by a promise 4650 chip. I don't have any desire to use them as raid, but from what I understand I should be able to use them as separate disk controllers, just like the other ports. I have gotten the newest linux(other) v1.1.0.12 driver from here:
[http://www.promise.com/support/download/download2_eng.asp?category=all&os=100&productID=191](http://www.promise.com/support/download/download2_eng.asp?category=all&os=100&productID=191)

and in my quest for info I have been here: 
[http://www.linuxquestions.org/questions/linux-hardware-18/drivers-for-promise-pdc42819-raid-controller-on-msi-k9a2-platinum-motherboard-621818/](http://www.linuxquestions.org/questions/linux-hardware-18/drivers-for-promise-pdc42819-raid-controller-on-msi-k9a2-platinum-motherboard-621818/)
and here:
[http://www.colinmackenzie.net/index.php?option=com_content&view=article&id=12:promise-satasas-driver-update-tx4650tx2650&catid=8:rotator&Itemid=7#](http://www.colinmackenzie.net/index.php?option=com_content&view=article&id=12:promise-satasas-driver-update-tx4650tx2650&catid=8:rotator&Itemid=7#)

Yet I (most likely from inexperience with such matters) still can't get this to compile without errors and I believe that I just need a bit of help transferring the directions on the README to work with Ubuntu since they seem to be mostly referring to Redhat and SLED. 

I attached the README file that came in the driver tar archive in case that would help. I tried to run "make clean" like it says after making the soft link but I got this:
```

~$ make clean
cat: /usr/src/linux/include/linux/version.h: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/include/linux/utsrelease.h: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
rm -f osd/*.o 
rm -f cam/*.o 
rm -f engine/*.o 
rm -f general/*.o 
rm -f pbm/*.o 
rm -f linux/*.o
rm -f *.o
~$ make
cat: /usr/src/linux/include/linux/version.h: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/include/linux/utsrelease.h: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
cat: /usr/src/linux/.config: No such file or directory
grep: /usr/src/linux/include/linux/version.h: No such file or directory
kernel version:  
make  CC=cc LD=ld CFLAG="-O2 -fomit-frame-pointer -D__KERNEL__ -DMODULE -D__linux__ -Wall -Wstrict-prototypes -fno-strict-aliasing -fno-common -Wno-unused -pipe -D_X8632B -D_32BPLATFORM -I/usr/src/linuxinclude -I/usr/src/linux/include/scsi -I/usr/src/linux/drivers/scsi -I/usr/src/linux/include -I/usr/src/linux/include/scsi -I/usr/src/linux/drivers/scsi -march=i386 -fno-strength-reduce -march=i586 -falign-loops=2 -falign-jumps=2 -falign-functions=2 -DCPU=386 -Wno-multichar  " -C linux
make[1]: Entering directory `/opt/tx4650/linux'
cc -O2 -fomit-frame-pointer -D__KERNEL__ -DMODULE -D__linux__ -Wall -Wstrict-prototypes -fno-strict-aliasing -fno-common -Wno-unused -pipe -D_X8632B -D_32BPLATFORM -I/usr/src/linuxinclude -I/usr/src/linux/include/scsi -I/usr/src/linux/drivers/scsi -I/usr/src/linux/include -I/usr/src/linux/include/scsi -I/usr/src/linux/drivers/scsi -march=i386 -fno-strength-reduce -march=i586 -falign-loops=2 -falign-jumps=2 -falign-functions=2 -DCPU=386 -Wno-multichar   -D_LINUXDRIVER -I../ -I../linux -I../pbm -I../cam -I../osd -I../engine -I../general -c osd_main.c 
osd_main.c:1: error: CPU you selected does not support x86-64 instruction set
osd_main.c:1: error: CPU you selected does not support x86-64 instruction set
make[1]: *** [osd_main.o] Error 1
make[1]: Leaving directory `/opt/tx4650/linux'
make: *** [linux/ft.o] Error 2

```
The one other thing I tried to do is remove the soft link, download the kernel source (with I realize I didn't have previously) and then make a new soft link to the location of the kernel source. That gave the same errors though. 

I'm running fully updated ubuntu 9.04 amd64. If anyone needs any more hw or other info, I can provide that as well. Thanks in advance for any help! :)

---

### Post by LashSilence83 on 2009-05-07
bump. 
I really want to be able to use those extra two sata ports on my mobo. I know it can work because there are supposed to be folks out there who have made it work. I simply don't have the knowledge to create the links correctly and/or understand the directions on the README. Someone please point me in the right direction... I did a bios update and tried booting with a dvd/rw drive plugged into one of the promise controlled ports and it made the boot sequence hang up for a bit, then give warnings about the bios having an acpi problem with linux. Even weirder is that I can't do anything with the drive except eject the tray from the terminal. It doesn't even show up in nautilus. This is just really frustrating for me since I want to add another hard drive and put my secondary optical drive back in the system but it seems that I may not ever be able to make it happen. 

UPDATE: Apparently the kernel I'm running is supposed to support most promise fast track chips with a module called "stex". The problem with that is that I have no idea where to get it from. I checked synaptic and I did a few searches but turned up nothing.

---

### Post by reznorio on 2009-05-13
Hi,

You downloaded the kernel source and extracted it in /usr/src?
you link it to /usr/src/linux?
you copy over config from boot to .config in the /usr/src/linux dir?
run make menuconfig save it and then quit then run make. It should fix those header errors you're getting (I got).

ReZ

---

### Post by albinootje on 2009-05-23
...[removed]

---

### Post by LashSilence83 on 2009-06-17
I'm marking this one as solved because as of the 2.6.28 kernel (possibly before, I'm not exactly sure) the T3 controller works out of the box due to updated AHCI drivers. I'm Stoked!!!

---

