---
title: "strange issue apparently with grub"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by esme on 2009-03-25
my apologies if other people have already reported problem similar to this, I did search but didn't see anything that I felt would solve the problem

anyway background first

my machine spec is as follows

Clevo M57U laptop chassis purchased from Rockdirect as an Xtreme CTX Pro T72 variant with a 100Gb SATA Hdd
Intel Core 2 T7200 @2Ghz, 1Gb Ram, Nvidea GeForce Go 7950 GTX, Windows XP Professional with the recovery console installed to the HDD

my partition layout is as follows

~49Gb Windows XP NTFS partition
~19.5Gb NTFS data partition
~14.5Gb Fat32 partition
with the remainder as an extended partition where I've been attempting to install Ubuntu 8.10 as a dual boot system to test with and currently this has two partitions for the root installation and the swap space left over from my last attempt

I know it's not the best way to install Ubuntu but I'm checking it out for the future

this ubuntu installation worked when I tried it but I had problems with XP which I think I've narrowed down to Grub although I'll be happy to listen to any other possibilities

the problems I had were these
[LIST]
[*]when I booted to XP I found that my DVD drive had disappeared, further it didn't appear in the hardware manager either, scanning for hardware and trying to add it back in also didn't work
[*]I couldn't start the recovery console, I got disk errors
[*]XP disk check wouldn't run from boot with a scheduled disk check
[*]I have a third party disk defragmentation utility that will defragment on boot, this would not run either
[/LIST]
to get my dvd drive back in XP I booted a dos disk and ran "FDISK /MBR" which sadly wiped out the grub bootloader and means I can't get at the ubuntu installation

this didn't cure my recovery console problem and I had to recover my system from a backup to get that working

I have done a few experiments installing Ubuntu 8.10 and it only seems that I get a problem when I install GRUB to the hard drive, there seems to be something wierd going on with the MBR like it's not a standard size or something, which is just silly as the MBR is always the same size

I'd really like to get this dual boot working properly so any suggestions or thoughts would be most welcome

---

### Post by esme on 2009-03-25
[S]one thought has occurred to me, I have a spare small USB stick that I'm not using for anything in particular

could I install grub to that so I boot via the USB stick but then run software from the HDD ?

presumably I'd need to do this from the Ubuntu install CD so if it's possible can anyone give me a set of instructions ?

it wouldn't solve the problem I'm having but it would let me do my testing[/S]

ignore that I've found a link for making a grub boot disk at [http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy")

---

### Post by esme on 2009-03-28
no one else has seen this ?


ooeerr I wonder what's strange with my system then

---

### Post by esme on 2009-03-31
after copious research it turns out to be a well known problem

on my machine if I use grub it does strange things to the BIOS and I lose any CD/DVD drives for both Ubuntu & Windows

and the solution is to use an alternative boot loader like lilo

---

### Post by xir_ on 2009-04-18
hey i thought id let you know i have had the same problem as you. Using lilo works a treat i put a post up in the rock direct forums about how to acheave this, but i didn't suffer from ever loosing it in widows.

so maybe first check to see if your bios is up to date

---

### Post by esme on 2009-04-20
thanks I'll see if there's an update

---

### Post by upchucky on 2009-04-20
there is a known issue in windows about the cd/dvd drive going missing from device manager and a registry hack to fix it.

[http://barugon.wordpress.com/2008/08/01/windows-cannot-load-the-device-driver-for-this-hardware-the-driver-may-be-corrupted-or-missing-code-39/](http://barugon.wordpress.com/2008/08/01/windows-cannot-load-the-device-driver-for-this-hardware-the-driver-may-be-corrupted-or-missing-code-39/)

I had the drive go missing from my toshiba and had to change the filters settings in the registry, microsoft knowledge said it was a problem in vista but the fix worked on my xp pro

---

### Post by esme on 2009-04-21
thanks for the advice and link upchucky

but no, the problem is specifically with grub and the bios on my machine

it's not that the hardware is there but can't be accessed because from windows because the registry filters are wrong, it's that the bios isn't reporting the drives existence, so windows and ubuntu both remove it thinking there's no such device

if I turn the apm off in grub then the drive reappears in both operating systems

it is a well known problem and the solution is to use a different boot manager like lilo

---

### Post by Tankerdog2002 on 2009-07-27
I have this same issue with ubuntu 9.04, XP dual boot.

Malibal Satori (Clevo M57u)

All is fine with XP until I install Ubuntu 9.04. After rebooting, CD DVD is missing from device manager. Cannot fix with Microsoft registry fix.

The weird thing is that the CD DVD drive works fine in the Ubuntu 9.04 partition. The CD DVD is not even listed in XP device manager, but it is listed in the BIOS.

I can't resolve this. I've tried every solution thats been posted on many forums. Nothing corrects this issue. 

I need XP for custom software that we sell. I guess I'll have to remove Ubuntu jaunty and just use XP.

If anyone finds a solution to this please post a fix.

Thanks, 
Tank

---

### Post by Tankerdog2002 on 2009-07-27
OK, I solved this issue with help from two threads:

[http://forum.notebookreview.com/showthread.php?t=186062](http://forum.notebookreview.com/showthread.php?t=186062)

[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition/](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition/)

It seems that GRUB wants to change the drive letters for Ubuntu.

I had to manually partition Ubuntu 9.04 and use "sda" as the name for all my drives. 

By default, Ubuntu wants to name new Linux drives as "sdb". This doesn't work with some older laptops. LILO works when all drive letters are the same. For example, my drives are now named:

(XP)............................/dev/sda2

(Linux swap)..................../dev/sda5
(Linux extended)................/dev/sda6
(Linux ext3 "mountpoint /"....../dev/sda7

My CD DVD optical drives are now working with LILO.

SUCCESS!!

I hope this helps someone.

Tank

---

### Post by Tankerdog2002 on 2009-08-23
Here's an update to the same old problem of the missing optical drives.

LILO only worked until the next kernel update.

Three different machines: Dell Vostro, HP-dv6000, MALIBAL Satori.

After rebooting all the machines were toast.

The new kernel update somehow wiped out LILO. There isn't even a /etc/lilo.conf file anymore.

XP partition will boot but the Linux boot sequence ends with error:
invalid compressed format (err=1)

At that point you can't do anything. You have to power off by holding down the power button.

I hope someone at Canonical is paying attention to the bug reports. This is becoming ridiculous.

Oh....yes....we did all that LILO config stuff for kernel updates, so please don't post back with any advice for that sort of thing. It doesn't work. There are bugs posted in launchpad for that also.

If I sound pissed, sorry, I'm just frustrated.

---

### Post by burkhardt on 2009-08-23
I have a similar issue and was hoping you could help.

I use a Lenovo Thinkpad T61 and am trying to get a dual boot of Ubuntu 9.04 and Windows XP working.

I am currently running Ubuntu off of my Live CD because my laptop has an issue with GRUB which won't even allow me to run my Windows partition. 

Originally I had Ubuntu installed into Windows (which worked fine no issues what so ever and had worked for two months) but I disliked the limitations thereof so I deinstalled it and installed the full Ubuntu from the live CD (about five hours ago). Once installation was finished I restarted, taking out the CD as it said to. Immediatly after I closed the tray and hit enter to continue Ubuntu closed and I got a long list of error messages ending in a message stating that it was restarting my laptop. Upon restarting it went through the Thinkpad splash screen and showed this: 

GRUB Loading stage 1.5

GRUB Loading, please wait ...
Error 21 
_

All I can do at this point is to put in the Live CD and restart.

I have not read the links to articles in this thread yet, but will do so shortly.
I am very unexperienced in this area, my hope was to have it function as a crossover system from Windows to Linux so I could be comfortable with Linux systems in the future.

Please all help and suggestions are greatly appreciated.

Thanks,
Burkhardt

---

