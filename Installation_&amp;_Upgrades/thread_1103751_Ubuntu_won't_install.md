---
title: "Ubuntu won't install"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by dslod18 on 2009-03-23
Hi,

I am trying to install Ubuntu on my desktop computer, which has an ASUS P5KPL-CM motherboard, Intel Celeron D 3.20GHz, and Nvidia GeForce 7600 GS Graphics Card.

With this set up, I am unable to get Ubuntu to install, no matter what I try. I understand that getting Nvida cards to work under Ubuntu can sometimes be challenging, but I've tried installing Ubuntu with and without the Nvidia card installed in the computer, and nothing works (in fact, I usually get further on the times that I do use the Nvidia card).
I've tried changed to safe graphics mode, I've tried pressing F6 during the live CD boot and changing some of the boot option parameters, I've tested the cd for defects, I've tested the memory in the computer, etc. 

90% of the time, it either freezes during the Ubuntu progress bar loading screen, or on the chance I actually make it to the installation screen, it ALWAYS FREEZES at either step 3 or step 4 (where it allows you to choose your partition setup for installation, use guided, whole disk, manual partitioning, etc).

The computer has two internal SATA drives, I've tested both of the drives for errors, and they both pass successfully.

Can someone PLEASE help me try to figure out what could be causing these problems?? I'd really like to get Ubuntu installed on this computer (I've also tried Kubuntu, Linux Mint, Ubuntu Studio and Fedora 10, all with the same results), and unfortunately I don't think I'm smart enough to figure it out.

I've also tried searching the Ubuntu forum pages, but the only things remotely related I can find is people who had problems either with the onboard NIC, or with getting an Nvidia card to work after installation (I'd be fine with that if I could just get Ubuntu installed first!!).

Thanks for any help or suggestions.

Danny

---

### Post by inobe on 2009-03-23
welcome

have you tried the alternative cd ?

the alternative cd can be found on the same download page with little navigation.

nothing flashy about the text based installer.....


btw' i may be gone soon, leaving as much info as possible will help !

are you dual booting with windows ?


if yes' have you considered installing within windows .........

---

### Post by dslod18 on 2009-03-23
Currently, I'm not dual booting, because I just built this computer putting the parts together I described in my post. So right now, there is no operating system installed.

Ultimately, I'd like to install Ubuntu to SATA drive 1, install VirtualBox and then run Windows XP inside of Ubuntu, and then I can use SATA drive 2 for storage.

I'll try the alternate cd, although I thought that was fairly similar to the Ubuntu Studio installation cd, and that failed on me as well.

I just tried the Ubuntu 64bit version cd (I have a Celeron D 351, which supports 64bit processing), and that actually got all the way to the installation, but then it froze at 5%.

---

### Post by inobe on 2009-03-23
i think it's the live cd causing this !

the alternative is text base, use either 32 or 64bit versions....

i have a pentium D system running 8.10 intrepid x64.....

the alternative will rule out the live cd being the culprit..


make sure you don't have the external plugged in until the installation is complete with any of the cd's, this will avoid mistakes.

---

### Post by dslod18 on 2009-03-23
I just tried installing ubuntu with the Alternate cd (32bit version, haven't tried the 64bit, since I'm only using 2GB of RAM in this computer), and got this error while it was installing the base system:

Debootstrap warning
Warning: Failure while installing base packages. This will be re-attempted up to five times.

I hit ok 5 seperate times, each time getting the same error.

Then the next error I got was this:

Unable to install busybox-initramfs
An error was returned while trying to install the busybox-initramfs package onto the target system.

Check /var/log/syslog or see virtual console 4 for the details.

What is going on?

---

### Post by ambdeep on 2009-03-23
are you able to boot from the live cd?

---

### Post by dslod18 on 2009-03-23
I can boot from the live cd, I just can't install from it.

I just tried installing using the Alternate 64bit cd, and got the same Debootstrap warning.

---

### Post by ambdeep on 2009-03-23
Its most likely that the manufacturer has blocked installation of other operating systems on your pc on the motherboard.....try installing virtualbox and putting ubuntu onto that....you wont have ubuntu in your boot options....but you will be able to run it in windows.

---

### Post by dslod18 on 2009-03-23
Well, I've seen other threads where people have Ubuntu installed on this same motherboard, so I wouldn't think that's the case (at least I hope not).

There is a setting in the BIOS to allow plug and play operating systems (by default this is set to no). Would changing this to yes do anything different?

---

### Post by ambdeep on 2009-03-23
i dont think that will work...as plug and play OSs are the ones on pendrives or other portable media.......and it is not necessary that if the motherboard is the same the BIOS is the same....sometimes manufacturers like HP release patches by which you can install OSs approved only by them....in that case you would have to download the BIOS from the official site and flash your current bios using a jumper...then install the official bios......its quite a complicated process and it is recommended not to do so as you may end up spoiling you motherboard completely.

---

### Post by dslod18 on 2009-03-23
But I've already flashed the BIOS with the most recent version from ASUS' website for their P5KPL-CM motherboard, and it still isn't working. I also tried installing Ubuntu before upgrading the BIOS, but no luck there either.

ASUS releases linux drivers for a lot of their products, so I wouldn't think they'd deny installing linux on their motherboards. . .

---

### Post by inobe on 2009-03-23
i will go out on a limb and say something is defective...


additional things i would do

reset the cmos

make sure the hdd is on sata channel 1'

remove all external devices including thumb drives

use only cd/dvd devices on secondary ide

check the board for proper jumper configuration

edit: to add i would also make sure that the bios is configured with the correct time, remember the bios has a 24 hour clock, rite now it's 14:00 hours.

make sure the hdd settings in the bios are changes, try sata, try ahci.....

---

