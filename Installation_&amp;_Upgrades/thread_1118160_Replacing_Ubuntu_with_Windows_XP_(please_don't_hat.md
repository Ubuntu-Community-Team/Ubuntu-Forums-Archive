---
title: "Replacing Ubuntu with Windows XP (please don't hate me)"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by agesaces on 2009-04-06
I installed Ubuntu on my daughter's computer figuring she can learn with a better operating system and how to actually USE a computer.

We got her some learning software and hardware, which will NOT work with Ubuntu or Wine or anything but Windows.

So, I figured I'd install Windows XP on the machine and have a "dual-boot"...but everything I read says I have to install Windows FIRST...and Ubuntu second.

So, I figured I'd just try and install XP and wipe out Ubuntu...and then no headaches...or trying to control the dual-boot for my daughter.

Anyway...I put the disc in, and I get the prompt "do you want to boot from the CD...Press any Key"...and I press...and I press...and I think I've tried every key on the keyboard now...but every time it bounces out to "Grub" and then boots up Ubuntu from the harddrive.  

So that tells me that SOMETHING in the BIOS or Ubuntu is not allowing me to boot to the CD.

That's why I'm here.  You all are the experts on Ubuntu...and I know it's sacrilege to ask how to get rid of it...but I really need to get this thing working for my daughter, and I can't find any clear...step-by-step instructions on how to remove Ubuntu completely, so I can install Windows.

Is there a "C:/" Prompt feature in Ubuntu?  I can go out and format the hard drive?

I could really use some help on this...please.

As soon as is reasonably possible, I'll create the dual-boot thing...so I don't have to do it again...but I need some help here.

Thanks.

---

### Post by Spunkbubble on 2009-04-06
I'm a total noob to linux in general, but you could always just burn a boot disk and wipe the hard drive.

---

### Post by dacorr on 2009-04-06
it reads like the Disk is not bootable is it the windows disk or the ubuntu disk?

---

### Post by agesaces on 2009-04-06
> **Spunkbubble said:**
> I'm a total noob to linux in general, but you could always just burn a boot disk and wipe the hard drive.

Ok...I could try and figure that out...but

1) If it's not booting from the CD...that's a problem...even with the disk.
2) If I wipe the hard drive...will it still have CD Drivers available to read the CD Drive in order to install from the Windows CD?

---

### Post by agesaces on 2009-04-06
> **dacorr said:**
> it reads like the Disk is not bootable is it the windows disk or the ubuntu disk?

Windows XP OEM disk.

---

### Post by JohnLM_the_Ghost on 2009-04-06
> **agesaces said:**
> If I wipe the hard drive...will it still have CD Drivers available to read the CD Drive in order to install from the Windows CD?

Yes! The BIOS initiates boot from CD, which carries it's own set of low-level drivers.

In fact you can boot with no hard disk at all!

---

### Post by JohnLM_the_Ghost on 2009-04-06
> **agesaces said:**
> Windows XP OEM disk.

Seems it is corrupted...
Hmm... try booting that up on other PC and tell if you have any luck!

---

### Post by trekguy on 2009-04-06
Awww...don't give up.  I'm no expert, and I've dual-booted both of my machines... one had Windows first, and one had Ubuntu first.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

---

### Post by dk92123 on 2009-04-06
> **agesaces said:**
> I installed Ubuntu on my daughter's computer figuring she can learn with a better operating system and how to actually USE a computer.

We got her some learning software and hardware, which will NOT work with Ubuntu or Wine or anything but Windows.

So, I figured I'd install Windows XP on the machine and have a "dual-boot"...but everything I read says I have to install Windows FIRST...and Ubuntu second.

So, I figured I'd just try and install XP and wipe out Ubuntu...and then no headaches...or trying to control the dual-boot for my daughter.

Anyway...I put the disc in, and I get the prompt "do you want to boot from the CD...Press any Key"...and I press...and I press...and I think I've tried every key on the keyboard now...but every time it bounces out to "Grub" and then boots up Ubuntu from the harddrive.  

So that tells me that SOMETHING in the BIOS or Ubuntu is not allowing me to boot to the CD.

That's why I'm here.  You all are the experts on Ubuntu...and I know it's sacrilege to ask how to get rid of it...but I really need to get this thing working for my daughter, and I can't find any clear...step-by-step instructions on how to remove Ubuntu completely, so I can install Windows.

Is there a "C:/" Prompt feature in Ubuntu?  I can go out and format the hard drive?

I could really use some help on this...please.

As soon as is reasonably possible, I'll create the dual-boot thing...so I don't have to do it again...but I need some help here.

Thanks.
*perss [esc] right when the computer starts foe the bootloader prompt-to boot windows)

Download G-Parted -it is a live cd you can delete the ext3 and swap and restart with your windows cd


to dual boot make sure windows xp is installed first and then install ubuntu. it will default to load ubuntu first so to change/edit the boot order in grub so it defaults to windows if you want windows to load automattically.

here is the info for editing grub: 
[http://makingtheswitch.wordpress.com/2007/04/29/changing-grub-boot-order-to-boot-windows-xp-before-ubuntu/](http://makingtheswitch.wordpress.com/2007/04/29/changing-grub-boot-order-to-boot-windows-xp-before-ubuntu/)

---

### Post by dk92123 on 2009-04-06
Usually you will see something in bios that says press "__" to change boot order but it sounds like bios already defaults to boot from CD first (I press [enter] or the space bar when it asks and I want to boot from the cd 
-----------------------------
You should also see something in bios that says press "__" to enter bios setup and you can change CD/DVD to be 1st in boot order.  (USUALLY [ESC] [DEL] OR ONE OF THE F KEYS - [F1], [F2] [F3] [F4] [F5] [F9] [F10] [F11]  [F12]
[DEL] [ESC] AND [F12] [F9] ARE MOST COMMON
---------------------------------
I'm not sure if you are using an OEM windows CD, if not, boot from windows cd and delete all existing partitions and create make a new NTFS partition for the entire drive.

If you are using the OEM Install CD I think the safest way is to use the G-parted CD so you don't wipe out the OEM Partition (FAT)

------------------------------------

FYI: It seems to be normal, you just need to figure out the timing of when to press what for the booting part, then when you are in ubuntu it should be easier than windows if you are not afraid to explore a little and Google/LinuxForums are your friend for everything you don't know

If you want to elaborate on the problem, maybe we can help

---

### Post by upchucky on 2009-04-06
> **agesaces said:**
> 

We got her some learning software and hardware, which will NOT work with Ubuntu or Wine or anything but Windows.

Thanks.


are you sure that the free educational software in ubuntu's repositories are not what you are looking for?

there are thousands of free software packages available and the educational ones cover all the way from pre-school to university

---

### Post by dsnort33823 on 2009-04-06
I'm not an expert on comps in general and a complete Linux Noob, ( Still waiting for first Linux machine to arrive), but I think your problem might be the OEM disk. Seems I remember reading somewhere that certain OEM's provide a disk that is System Restore only, there is no fully installable or bootable copy of Windows on the disk. I have a Dell that I think is like this.

---

### Post by ameermawia on 2009-04-06
hi!
just first try to change the boot order in bios ,and give cd the first prefrence.if the problem is not solved you can choose other alternative.
Boot via USB.just make ur usb drive bootable and change the boot order in the bios and intall xp via usb just like any installing from cd .
you can google out for information on how to make usb bootable .As far making usb bootable with ubuntu in it ,there is utility provided in ubuntu........in system ->adminstration ->create startup disk.i am not sure wether it will make window bootable  usb or not but there are many more application which take just cd image and make the usb bootable .just google out for them.
Thanks!

---

### Post by dk92123 on 2009-04-06
> **ameermawia said:**
> hi!

Boot via USB.just make ur usb drive bootable and change the boot order in the bios and intall xp via usb just like any installing from cd .
you can google out for information on how to make usb bootable .As far making usb bootable with ubuntu in it ,there is utility provided in ubuntu........in system ->adminstration ->create startup disk.i am not sure wether it will make window bootable  usb or not but there are many more application which take just cd image and make the usb bootable .just google out for them.
Thanks!
The Link:
[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)

---

### Post by barrydirk on 2009-04-19
Without sounding patronizing make sure you do the pres any key thing when windows installer asks windows needs to restart a few times during install to complete the process thus its default boot priority even with the disk in is from hard drive if that still doesn't work I assume your MBR is probably corrupt and the best way to straiten all that out if your not afraid to lose all your data is with a program called Darick Boot and Nuke. Download ISO burn to disk and pop in the drive it takes a while but it should reduce your disk back to 0. Now boot from your win disk start up the partinioner and create two partitions allocating most of the space to win and leaving say 15Gb or 20Gb for Ubuntu as the win ntfs file system  is usable by lynux but win cant read ext3. Complete the win install pop in ubuntu install on remaining partition slip snip and bobs your aunty and if that still doesn't work e-mail me and I'll try again.

---

### Post by nos09 on 2009-05-04
well, I did have the problem before. It was on fedora but anyway you may not probably interested in my problems but I did made it with [COLOR="Red"]windows 98.[/COLOR]

[COLOR="Red"]I recommend you to boot with [COLOR="Red"]win 98,[/COLOR].format all hardrive with it. and dont need to install win98 after formatting hard disk. then install windows(any version you may prefer)then ubuntu.[/COLOR]


think it can work for you or at least can hope. and just do as usual dont need to do any thing extra just as usual booting/installing windows. Good luck.

---

