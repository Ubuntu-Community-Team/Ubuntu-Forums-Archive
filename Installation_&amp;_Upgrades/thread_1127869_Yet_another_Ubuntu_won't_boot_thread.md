---
title: "Yet another Ubuntu won't boot thread"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by sides on 2009-04-16
Hi all, I am trying to install Ubuntu 8.10 and can't boot when I remove the installation cd. I just get a blinking _ cursor in the upper left hand corner of the screen.

Here is a description of my system and the steps I have taken so far.

Asus A8n-Sli Premium motherboard - AMD X2 4400+ - 2 G ram

SATA 1 - WD 150G drive Part 1 - 130G (XP Pro) Part 2 - 20G (Leopard)
SATA 2 - WD 500G drive 
IDE 1 Master - WD 250G drive
IDE 2 Master - Plextor DVD burner
USB - WD My Book
USB - WD 120G drive in an external enclosure Part 1 (sdd1) - 17G ext3 Ubuntu mounted to / Part 2 (sdd2) - 3G Linux Swap Part 3 (sdd3) - 100G Fat32

On my first attempt, I created my Ubuntu partitions with a gparted boot cd. My installation ran smoothly, though I accidentally installed Grub on my 500g SATA drive. I was ok with that because I planned on using the XP bootloader to select my os (I currently use it to dual boot XP and Leopard). After my install, I rebooted to the GParted CD and used the steps at [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) to set up my boot.ini.

I rebooted, selected Ubuntu and promptly got a rapidly flashing _ cursor in the upper left hand corner of the screen. My next step was to go in my Bios and set the External 120G USB drive as my boot drive. I got an error that the operating sytem wasn't found. I changed my boot order to boot to the 500g SATA drive to run Grub. Grub gave the "Grub Loading stage1.5." message, then halted with error 17 followed by the blinking _ cursor.

I booted again to GParted and checked/fixed the filesystem on /dev/sdd1 (the first partition on the external drive). I also noticed that /dev/sdd3 (the fat32 partition) had the boot flag set. I changed the boot flag to /dev/sdd1, set the external 120G to my boot drive in the bios and got the same error loading operating system messagea as before.

At this point I tried installing one more time, mounting /dev/sdd1 to / and /dev/sdd2 to linux swap, formatted, installed, and didn't install grub this time. I got exactly the same results as the first attempt and I am out of ideas.

Any help at all would be greatly appreciated.

On a side note, I can't find info on how to remove grub from a non-boot drive. Can I boot to XP recovery mode and fixmbr on a drive other than my boot drive? It isn't a huge deal I guess since I don't ever plan on booting to the 500G SATA drive but if there is an easy way to remove it, I'd rather clean up after myself.

Thanks again.

---

### Post by seventyeights on 2009-04-16
I don't have this problem, but I did just hear about it for the first time only ten minutes ago.  Check out this thread...
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by sides on 2009-04-19
Thanks for the reply, but I don't think this is related to grub detecting my drives in a different order than my bios due the most recent test I did.

I pulled the 120G IDE drive out of the external housing and made it my primary IDE master drive by putting it in my case. I made it first in the boot order for hard disks. I reinstalled ubuntu using guided partioning (and not installing grub), allowing it to use the whole drive. When it was time to reboot and boot off the hard drive I got an error saying that it couldn't load the OS and I needed to insert the system disk. I put the drive back in the usb housing and tried to boot off of it and got the same message as when it was plugged into my ide cable. This is starting to drive me a little crazy.

---

