---
title: "Laptop Question"
date: 2008-08-17
forum: General Help
---

### Post by hasek522 on 2008-08-17
I have an HP Pavillion dv5-1004nr Entertainment Laptop
With a 2.0 ghz AMD Turion X2 64bit processor
4 GB of ram
and an ATI HD Radeon 3200 Graphics card?

Will ubuntu be ok to put on my laptop?
Also, can I only have one HD on my laptop.  Can I install it on the same hard drive with out messing up the windows installation I currently have and all the files on it?

---

### Post by eggie9001 on 2008-08-17
You can dual-boot windows xp and Ubuntu.

Just google a tutorial on how to do it or look on the forums.

Yours,

Eggie

---

### Post by hasek522 on 2008-08-17
ok I dual boot on my pc but i have Ubuntu installed on a second hard drive.

---

### Post by az on 2008-08-17
By default, the Ubuntu installer should offer you the option of resizing the current OS's partition to make room for Ubuntu on a separate partition on the same drive.

I figure most people dual boot Ubuntu with only one drive.

If you don't get that option, reboot into windows and defragment your disk, then try again.

---

### Post by qrprat77 on 2008-08-18
> **hasek522 said:**
> I have an HP Pavillion dv5-1004nr Entertainment Laptop
With a 2.0 ghz AMD Turion X2 64bit processor
4 GB of ram
and an ATI HD Radeon 3200 Graphics card?

Will ubuntu be ok to put on my laptop?
Also, can I only have one HD on my laptop.  Can I install it on the same hard drive with out messing up the windows installation I currently have and all the files on it?

hi Hasek522,
yes you can install ubuntu.  I should know, I bought one last night, and got it mostly squared away in about four hours.  Took a little research, but was worth the effort.  you don't need to install another hard disk, just make the machine dual boot.

first,
you will need the 8.04.1 disc, not the original copy.  If you haven't burned your disc yet, or downloaded Ubuntu, you will need to make sure you are downloading the most recent one.  the actual name of the iso will reflect it's revision number, for example, the iso i d/l'd and burnt last nite was ubuntu-8.04.1-desktop-amd64.iso .  That is important.  the older 8.04 version i initially installed on my old lappy was not compatible with this version.  

after you have a good disc, you will need to repartition your disc from inside Vista.  it's pretty easy to do, i must say i was impressed.  Most people I've talked to have had better luck partitioning under vista than under gparted.  a quick google of repartitioning under vista will get you started.

after that plop in you ubuntu disc and begin the installation process.  you will need to have a wired ethernet connection at first, cause the wireless driver ships broke.  No surprise there though, right?

You'll have to compile the madwifi-ng driver from scratch to get wireless working but that's not terribly difficult.  lotsa places in the forum here can tell you how!

when you get done installing, grub will let you choose which os to boot to next time you crank er up!

have fun!

---

### Post by cybrsaylr on 2008-08-18
Sure you can dual boot. I have two dual boot systems that run fine. Just make sure to study the instructions on setup because it can seem confusing if you know little about Ubuntu. I took my time, learned it and all is running great.

---

