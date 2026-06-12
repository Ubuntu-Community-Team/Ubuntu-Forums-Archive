---
title: "installing on a 2 HD system"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by DragonRidr on 2006-02-11
hi i am new to this and have realy only started to learn. i have used the VMware player and tried the live CD for ubuntu a cpl times but want to learn more.

i have 2 hard drives in my pc one is a 60gig maxtor and the other is a 9gig maxtor drive. my windows install is on the 60gig drive. wich i could repartion but was thinking of useing the 9 gig for the install of ubantu so that i dont have to mess with my main drive. not that i am afriad too lol. i tend to mess with my pc alot learning as i go and haveing to fix problems. what i havent found in my searching and reading is how you do the install too 2 different drives only how to do it with one drive. any and all help will be aprecated.

i will be useing the ubuntu distro for the AMD 64 pc with a Nvidia NForce3 board with a NVIDIA GeForece FX 5200 card for the display adapter. thought the hardware info might help.

---

### Post by taurus on 2006-02-11
Your hardware is fine.  Yes, you can install Ubuntu on the second harddrive and 9GB should be more than enough.  When you get to the part where you want to install it, remember to tell it to install it on /dev/hdb, not /dev/hda!  And I recommand you let Ubuntu install GRUB on the MBR so it will boot both Ubuntu and your Windows...

---

### Post by DragonRidr on 2006-02-11
thank you for the info will try it and see how it goes and post here on how it worked or if i have troubles.

---

### Post by lha on 2006-02-12
IHMO, an easier and a safer way of installing Ubuntu with Windows is to put that 9GB drive where your current Windows disk is and place that bigger drive on another ide channel. (For example, make it primary slave = hdb.) Then install Ubuntu on the smaller drive. You don't have to overwrite Windows' drive's mbr with grub or fool around with bios settings. This will make both os' to be completely on their own drives, making it easier for you to ditch the other one if you want to.

---

### Post by DragonRidr on 2006-02-12
that is an idea if i can get the cale to reach. and if i am understanding you right you are saying put the 9gig as the main drive on one ide controler and then put the 60gig as the main drive on the other ide controler ??......

also do i need to make 2 partions on the 9 gig drive so that i have a swap partation and a main one for the ubantu??

---

### Post by lha on 2006-02-12
[QUOTE=DragonRidr]that is an idea if i can get the cale to reach. and if i am understanding you right you are saying put the 9gig as the main drive on one ide controler and then put the 60gig as the main drive on the other ide controler ??......
[/QUOTE]

Yes, that's the idea. It doesn't really matter where you put that 60 GB drive. Only thing that matters is the place of 9GB drive, which should be main drive on the first ide controller.

[QUOTE=DragonRidr]also do i need to make 2 partions on the 9 gig drive so that i have a swap partation and a main one for the ubantu??[/QUOTE]

Yes.

You can tell the installer to automatically partition that 9GB drive, so you don't have to do it manually. If you want to use the manual partitioning, it's a good idea to make a small swap partition (something like 400-600 MB) in addition to the main partition (root).

---

### Post by DragonRidr on 2006-02-12
maybe a dumb question but i read a thread that talked about useing GAG to boot from a floppy so that you dont have to change your MBR on the main drive and can still boot ither OS. any thoughts on that or anyone doing that ??

---

### Post by lha on 2006-02-13
[QUOTE=DragonRidr]maybe a dumb question but i read a thread that talked about useing GAG to boot from a floppy so that you dont have to change your MBR on the main drive and can still boot ither OS. any thoughts on that or anyone doing that ??[/QUOTE]
I still prefer having the drive with Ubuntu as main drive. If you really want to boot to Ubuntu with a floppy, I guess GAG does the job. I haven't used it myself. Ubuntu comes with a good boot loader that does what it's supposed to do and I haven't seen a reason to use anything else. (Maybe I'm a bit grub fan.;))

---

