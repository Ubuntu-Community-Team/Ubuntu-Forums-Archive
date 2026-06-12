---
title: "installation problem--CD boot error message"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by hisnibs on 2009-02-18
I wish to install ubuntu 8.10 onto my PC (486 P4) onto a logical partion (drive E:). I have Ecomstation (nee OS/2 ver 4.52) installed on this PC and I use OS/2's Boot Manager program. Drive E is included in the Boot Manager already, but nothing is installed on it, yet. 

I downloaded version 8.10 ubuntu and burned an ISO image disc of it. To install it (or try to) I just activate the PC to boot from the CD drive during boot up. I get the Ubuntu screen, but if I try to select any option on the main screen, I get an error message in a red box stating that there was a boot error from the CD, ie it is corrupted? I tried burning another CD, but this time at a much slower speed. Same problem. What do I need to do, download the Alternate CD and try installing from it? I have had no other error messages as I haven't been able to get past the basic installation phase.

Thanks, in advance.

---

### Post by axel_2078 on 2009-02-18
Lots of people seem to be having trouble installing 8.10 from a CD (me included). Not sure what's going on with that.

---

### Post by hisnibs on 2009-02-19
well, I have made some progress, of sorts. I decided to download the alternate CD for Ubuntu 8.10; that at least allowed me to install the program. Now the hitches. The installation corrupted the OS/2 boot manager, but I was able to retrieve it using my DFSee CD--great utility! After that I was able to boot into OS/2, but Ubuntu-nope. Error message states that the drive is not formatted. That may be my mistake. I chose the Journaled File System, a flavour of the JFS that OS/2 does not seem to recognize. Neither the partition in which ubuntu was installed or the partition I chose as the swap file are recognized by either OS/2 or Windows XP (across my network). That may be one problem.

Also, during installation, neither GRUB nor LILO would install. In an earlier attempt I recall some error message to the effect that the boot record did not like to be installed into a logical partition, which is where I installed ubuntu (drive E:). The swap file is on a second hard drive and is in a primary partition. I suspect that either one, or both of these issues may be the problem: incorrect filesystem not recognized by the OS/2 boot manager and/or program is not installed in a primary partition.

I invite your comments. Should actually post this message into and OS/2-Ecomstation forum as well.

Thanks

---

### Post by Fyrzen_ on 2009-03-21
I'm having the same problem on an ordinary Soc A Athlon PC. The CD boots, but whenever I tried to run the LiveCD session w/o install, install or CD error check i get the red box with "Boot Error" and some sort of short 5? digit number/code appears in the top left corner of the screen. 

I've repeatedly checked the md5sum for the downloaded .iso and it's clean. However, when performing an Md5sum on the cd itself, i get errors. This is said to suggest the md5sum isn't correct, hence it doesn't finish the process. 

I usually burn onto CDRW's i've used before so it's possible they're worn out. Then again every other version of ubuntu has never been a smooth install either(except Dapper beta <3 ). I'm trying the alternate before bothering to buy CD-R's. 

For the record i've already managed to install both Kubuntu 8.10 and Xubuntu 8.10 from their LiveCD's. So this problem seems specific to Ubuntu 8.10.

---

