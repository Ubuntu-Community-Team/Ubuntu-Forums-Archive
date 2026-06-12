---
title: "Help me duel Ubuntu with XP"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by pgtl10 on 2009-06-15
Last time I installed Ubuntu from a CD my XP wouldn't load. I had to reinstall Windows. 

I want to try again but how do I make Ubuntu won't prevent Windows from loading?

XP already is installed.

---

### Post by malachi1990 on 2009-06-15
Usually, the best way to go is to simply let the ubuntu installer partition the drive.  Assuming you did that last time, you can either make sure all your files are at the beginning of your drive by defragging it 2-4 times, or use the Wubi installer.

Just to let you know, XP will do a check disk scan the first time you boot into it, and should be okay.  

Even if it looks like the computer has hung on you, let it run. You could probly draw the line after ~1 hr.

---

### Post by pgtl10 on 2009-06-15
Partition wasn't the problem. My Windows simply couldn't boot. GRUB prrvented it from booting.

---

### Post by brncao on 2009-06-15
I'll share some of my experiences, but I'm still considered a newbie to the Linux world. It could be that grub mislabeled or misconfigured the boot direction incorrectly for Windows XP. You select Windows XP in the menu, but it probably doesn't know where it is. This information is found in the menu.lst file. You'll need to have grub installed somewhere on a partition so you can open menu.lst and configure it. Find the line that says "title    Windows XP" or something along the lines (near the bottom of the file). Make sure root or rootnoverify is set to the correct disk and partition. You'll see hd(X,Y). X is the disk number and Y is the partition number.

Example: my Windows 7 is located on my first hard drive (hd0,?) and on the first partition (hd?,0). This is what you'll see

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

Change (hd0,0) to wherever you installed Windows XP.

I recommend setting up the grub bootloader on a dedicated boot partition and not allow Ubuntu install its grub bootloader into the MBR because when I uninstalled Ubuntu I got an error 22 message. That meant Grub was wiped off the hard disk along with Ubuntu.

---

### Post by R_U_Q_R_U on 2009-06-15
Sorry, but when I read the tread title I focused on "duel" and thought swords or guns?

---

### Post by dandnsmith on 2009-06-15
> **R_U_Q_R_U said:**
> Sorry, but when I read the **tread** title I focused on "duel" and thought swords or guns?
 So how did we get on to these stairs?

---

### Post by pgtl10 on 2009-06-15
> **brncao said:**
> I'll share some of my experiences, but I'm still considered a newbie to the Linux world. It could be that grub mislabeled or misconfigured the boot direction incorrectly for Windows XP. You select Windows XP in the menu, but it probably doesn't know where it is. This information is found in the menu.lst file. You'll need to have grub installed somewhere on a partition so you can open menu.lst and configure it. Find the line that says "title    Windows XP" or something along the lines (near the bottom of the file). Make sure root or rootnoverify is set to the correct disk and partition. You'll see hd(X,Y). X is the disk number and Y is the partition number.

Example: my Windows 7 is located on my first hard drive (hd0,?) and on the first partition (hd?,0). This is what you'll see

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

Change (hd0,0) to wherever you installed Windows XP.

**I recommend setting up the grub bootloader on a dedicated boot partition and not allow Ubuntu install its grub bootloader into the MBR because when I uninstalled Ubuntu I got an error 22 message. That meant Grub was wiped off the hard disk along with Ubuntu.**


How do you do that?

---

### Post by brncao on 2009-06-15
How many hard drives do you have? Can you open up gparted and take a snapshot of each disks? Before that (assuming you have no OS installed) install Windows XP first and boot from that. Does it work? If yes proceed to booting into the livecd and open up gparted then take a snapshot of your disks.

---

### Post by lisati on 2009-06-15
> **R_U_Q_R_U said:**
> Sorry, but when I read the tread title I focused on "duel" and thought swords or guns?

:) It's fairly common in these forums to see similar-sounding words be used swapped around with "gay abandon". Annoying as it can be eye don't think their should be any problem that warrants coming down on the poster as long as they're meaning is clear..... I thought of fights too.

---

### Post by Sub101 on 2009-06-15
> **pgtl10 said:**
> How do you do that?

If you were to remove Ubuntu, and therefore Grub having completed a standard installation you can use the "[Super Grub Disk]("http://www.supergrubdisk.org/")" to restore the MBR.

 The website is down at the moment but its a disk I think everyone should have! Very useful.

---

### Post by pgtl10 on 2009-06-15
I already have XP installed so I just want Ubuntu to install. I don't want to format my hard drive and start over.

---

