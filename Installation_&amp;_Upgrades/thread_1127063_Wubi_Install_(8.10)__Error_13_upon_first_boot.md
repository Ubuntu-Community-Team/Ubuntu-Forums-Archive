---
title: "Wubi Install (8.10):  Error 13 upon first boot"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by iFargle on 2009-04-16
Hey, this is my first post here on Ubuntu Forums, so please, if this is posted in the wrong section, let me know.

So, let me list some specifics..

First off, my computer is a 2.2Ghz C2D, 8800GTS 320Mb, 2Gb Kingston RAM, a 1.5Tb Seagate Drive, a 160Gb Seagate Drive, and a 250Gb External "FreeAgent" Drive. (If there's anything else you need to know, let me know) running on Vista Ultimate 32bit with SP1.

I've been trying to reinstall Ubuntu 8.10 off of a live CD I downloaded when it was released (I'm 100% sure I've installed it on this same Hard Drive before, although on different Windows installation.)

I install it with Wubi, 30Gb partition, on my C: drive (the 1.5Tb drive)

It gives me Error 13 after selecting Ubuntu in the Windows Boot Manager.  I can't remember the criteria, but it has sometimes just reboots the computer.)

I've tried unplugging the 160Gb Drive and the External 250Gb Drive, but no luck there either.

Here's the specifics of what's displayed on my screen for the error message:

> 
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en.US.UTF-8 console=setup/layoutcode=us console-setup/cariantcode= --ROOT FLAGS=syncio

Error 13: Invalid or unsupported executable format

Press any key to continue...

Let me know if you need any more information.

 - iFargle

---

### Post by iFargle on 2009-04-16
Bump.  Need some advice.

---

### Post by ronparent on 2009-04-16
Are your older kernel version still in the grub boot list amd do any of your older kernels boot?

---

### Post by iFargle on 2009-04-16
The hard drive has since been reformatted, no traces of Linx are on the machine other than what I've done over the last few days.

I just downloaded the 9.04 Beta, but it does the same thing.

EDIT: And it's using the Windows Boot Manager, not GRUB.  Should I give GRUB a try?  Without Wubi?

EDIT: I just tried 9.04 Beta from the Live CD.  The Live CD booted, but when I got to the partition tool in the installer it won't partition.  I select a 3% partition size (Which was around 45Gb)  It didn't move.  Any ideas?  Suggestions?  Anything would be appreciated.

---

### Post by ronparent on 2009-04-16
I put my foot in my mouth whan I addressed your problem from a grub viewpoint. Being unfamiliar with wubi protcol I have to bump!

---

### Post by iFargle on 2009-04-16
Well, I've searched a little online.  I've ran a hard drive diagnostic from my Vista Ultimate install DVD.  Somehow it deleted 200Gb of data on my C: Drive (!!!!), but everything seems to be in place.  I'm doing another install through Wubi, seeing if this works.  

If it doesn't, I wouldn't have a clue what to do next :( I'll try partitioning it again through Windows and the Live CD. 

EDIT: so, I just installed Ubuntu through Wubi.

Now it brings up...

> GRUB4DOS 0.4.4 2009-3-19, Memory: 639K / 2046M, MenuEnd: 0x4343E
   [ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command copmletions.  ANywhere else TAB lists the possible completions of a device/filename.  ESC at any time exits. ]

grub>

I don't get it :?:

I'm going to see if I can install it through the Live CD.

No luck :(  I'm stuck back at the "GRUB4DOS" screen :(

---

### Post by ronparent on 2009-04-16
This one I think I know. I got the same results today when I tried to boot from grub in which I had deleted all valid boot instuctions form the menu.lst. Have a look at /boot/grub/menu.lst. What boot instructions are there?

---

### Post by iFargle on 2009-04-16
:P:P

The hard drive partitioned in Vista (Finally!) so it's installing using GRUB.  I'm fairly excited.  We'll see if it works. 

Thanks for the help anyways, I'm sure I'll need it somewhere down the road, I'm sort of a noob with Ubuntu.  I've been using it for years on and off, haven't taken the time to learn it

EDIT: V_V  At 94% of the installation it said something like the installation on hda0  failed.  I'm going to try with 8.10.

EDIT2: I couldn't get 8.10 to work either, same error :(

---

