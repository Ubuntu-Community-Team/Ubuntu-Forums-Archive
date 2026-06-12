---
title: "List of Boot Problems with Acer Aspire (Wal-Mart Special)"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by Darksword on 2007-11-10
I picked up one of the $348 Wal-Mart Acer 5315s a few days ago, after reading some generally favorable opinions of it here  [http://ubuntuforums.org/showthread.php?t=600714&highlight=Acer+Aspire](http://ubuntuforums.org/showthread.php?t=600714&highlight=Acer+Aspire) 
I was expecting the common difficulties of getting the sound and Wi-Fi working.  Instead I got a hellish nightmare of failure to boot.  I tried to install 7.10 first, but got a "kernel corruption" error, so I switched to 7.04, which you will see below.

Problems (abbreviated list):

Grub Loader does not function, at all.  Immediately after the ACER BIOS screen I get "No bootable device - Insert Boot disk and press any key."  However, my Ubuntu installation went fine, since I can use the "Boot from Hard Drive" option on the LiveCD to run GRUB and get to the desktop with some difficulty.  I attempted the fixes here:  [http://ubuntuforums.org/showthread.php?t=224351&highlight=Grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=Grub)
but to no avail.  I did learn that my /grub file is in a comparatively strange place.  Just inside the /mnt/root of sda2 instead of the /boot folder.  I adapted the fix to this, but with no success.

Problem 2:  The "can't access tty; job control turned off" error.  This one can be circumvented at liveCD installation by adding "break=top" to the F6 liveCD options and running "modprobe piix" "exit" at the error command prompt, as described here [http://ubuntuforums.org/showthread.php?t=421588&highlight=cannot+access+tty](http://ubuntuforums.org/showthread.php?t=421588&highlight=cannot+access+tty)
However the "fix" cannot be made permanent.  Editing the initramfs-tools/modules file to load piix at startup has no effect.  I have to do it manually every time.

Now, here's where it gets weird.  These two problems are stacked onto eachother.

If I use the LiveCD to load GRUB and boot the main OS, I get the "tty" error loading the main Ubuntu installation.  From there all I have to do it type "modprobe piix" and "exit" at the initramfs prompt and Ubuntu will load perfectly normally.  I can pop out the liveCD and use my computer like any other day, barring no sound or internet.  :P  But I have to do that every single time I start the computer, meaning I might as well just be working off the blasted liveCD.

My HDD partition info is as follows:

sda1:  /boot partition, 125 megabytes
sda2:  / partition 33 gigabytes
sda3:  swap partition 900 megabytes
40-some-odd gigs of free space that I'll be installing XP on later

I killed all original partitions, including the Vista recovery partition, at the first installation.

Any thoughts, friends?

---

### Post by monte48lowes on 2007-11-10
Dark,

I have never used a separate /boot partition before. Have you attempted the install without using a seperate partition? If you have a reason to do so I understand. 

From the sounds of it, something has happened to the MBR on the drive. Have you tried the grub rescue disc?

[http://geocities.com/supergrubdisk/]("http://geocities.com/supergrubdisk/")

Mike

---

### Post by Darksword on 2007-11-11
I'll give that a try tomorrow and let you know how it goes.  Thanks for the tip!

---

### Post by Darksword on 2007-11-13
No dice, unfortunately.

Still getting the initial "No bootable device detected - Insert boot disk" message.

---

### Post by Darksword on 2007-11-13
Sorry to double post!

I tried installing a fresh version of 7.10 and it worked!  Both errors were fixed.

However, I'm having a new one.  This is a work computer, and I need to dual boot with Windows XP to interface with our new inventory system.  However, when I run XP setup, it tells me that it can't find any hard drives on my computer.

Any ideas on this one?

---

### Post by Darksword on 2007-11-14
And a triple post!  I solved that last problem on my own, and installed XP.

The problem now is that instead of GRUB loading to let me choose between OSs, it just boots straight into Windows. XD

Any idea on this one?

---

### Post by monte48lowes on 2007-11-14
You can boot from the live CD and reinstall GRUB onto the MBR using:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Mike

---

