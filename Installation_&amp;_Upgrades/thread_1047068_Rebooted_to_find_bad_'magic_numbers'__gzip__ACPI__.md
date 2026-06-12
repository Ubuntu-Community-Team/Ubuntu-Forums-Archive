---
title: "Rebooted to find bad 'magic numbers' / gzip / ACPI / initramfs"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by MaddMatt on 2009-01-22
Hi All, 

Possibly as a result of the latest ACPI updates apparently my initramfs got corrupted between the updates and my last reboot (which I don't do often). 

In any case, I booted up this morning to find a message similar to this:
```
[0,269945]ACPI : Aborted because bad gzip magic numbers
[0,280017]..MP-Bios bug: 8254 timer not connected to IO-APIC
[0,433845]Kernel Panic - not syning : VFS : Unable to mount root fs on unknown-block (0,0)
```

I looked at a few of the forums and didn't find an answer. However, due to my recent escapades with booting I remembered how to update the initramfs (Initialization RAM filesystem):

Boot into an older kernel (if you have one) in rescue mode, or the rescue disk. 
Run this as root:

```
update-initramfs -k all -c -v
```

Hope this helps some of you that might be having the same problem. Cheers!

---

### Post by sekura on 2009-05-15
Please detail how to get into rescue mode / rescue disk... I'm using an USB stick that mounts the Live Session without giving me additional choices (like the CD). Also, from the CD, how do yo get into rescue mode?

Sory, i'm extremely new to ubuntu (since today), and i've gotten to my 2nd install due to this error. It'll be of help in the future to know how to fix it.

PS: Has this ruined the /boot/grub/menu.lst entries? Cause i havent managed to see anything wrong with them while having the problem.

---

### Post by MaddMatt on 2009-05-16
Hi Sekura, 

You are going to need the 'Alternate' cd to use the rescue mode. Don't fret it's a really easy process, as the alternate CD will pop up a menu when you boot off of it. 
Grab the alternate CD image here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

The grub menu list shouldn't be changed, but if it is it's a very easy fix. 

Hopefully you can boot from a normal CD drive? Otherwise you will need to look into putting the alternate installation CD on USB like you did the other installation. Good luck!

m

---

### Post by triviumuser on 2009-06-05
Had the same problem with my 9.04 Ubuntu installation.
Downloading the alternate disk, booting and updating initramfs solved this problem. Seems that this problem is due to last updates I've installed.

Thanks for posting the solution here!

---

### Post by tm007 on 2009-07-12
Genius you guys are great.

---

### Post by 9a3eedi on 2009-11-20
I need some help with this. I seem to have the same problem with 9.10 x86_64. 

I installed my ubuntu with wubi, so using a recovery CD probably doesn't work, and even if it did, I couldn't boot off it because it seems that my laptop's CD-ROM drive has just failed :( Additionally, I can't boot to an older kernel because there hasn't been a kernel update.

So what I tried doing is booting off the liveCD through a USB stick, and then chrooting to my install and updating initramfs from there. The update process seemed to have worked, but after a reboot I still get the same problem.

I'm now stuck on what to do next. Perhaps it's because I have chroot'd properly. I'll try again as soon as I have some free time. 

Please help :(

---

### Post by Wampyra on 2011-03-28
Old topic... New problem...

Solution seams simple, but i cant go into the resque mode... Only LiveCD.... Plus... Im writting from the ipad so i have no options of downloading anything, and its really uregent :(

Is there any way of going having a root privilegies while on liveCD? :/

Any responce is soooooo much anticipated.... Thanks! :o

---

