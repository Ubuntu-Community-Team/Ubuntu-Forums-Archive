---
title: "boot a second ubuntu[or kubuntu] install from usb drive..."
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Betelgeuse on 2009-01-20
Hi.

I have a small Asus eeepc 900 and I'm using it with kubuntu 8.04.
there is two ssd disk on this device, one is 4Gb and the other is 16GB.it was the linux model with xandros but I've installed kubuntu the day it arrived. Last week I've upgraded it to 2GB RAM, now it's better.
the drives are 4GB SSD for / (root partition) and 16GB ssd for /home partition.


Now I feel the ssd disks inside this computer are slow. its ok for working mobile, checking mails or browsing the web but when I'm at my desk, I'm using this tiny computer with a 19" monitor and usb keyboard and mouse. When I work on some serious stuff, the ssd seems slow. I'm running vmware-server on this tiny machine to test and develop some server database applications but I'm using an external 80GB USB hard disk for it. Now I've decided to use this USB hard disk as main boot drive. I have this use scenario :

When I'm out, I'll use ubuntu installation on the internal ssd disks and when I decide to do serious work, I'll shutdown, plug in the usb disk and boot the machine with another ubuntu installation on this usb disk and not touch the internal ssd disks.

I have lots of setup and things on this internal ssd drives now so I do not want to do a full install, instead I've tried to clone the first ssd disk to usb disk with clonezilla (it's a debian based mini linux distro thing for disk cloning). The cloning worked perfectly. Now I have two partitions on my 80GB usb disk. with my / and /home partitions.

Now, is the problem:
When I hit esc key to get the bios boot selector menu and select the usb disk to boot, the computer starts to boot from the usb disk but when the boot completes, I see that it's booted from the ssd drive not the usb disk drive. Now I'm stuck and do not know what to do... I've read lots of web pages fro google to solve this but still could not find anything.


PS: sorry for the long post, english is not my native language so I could not explain my problem with a short post...

---

### Post by fatbotgw on 2009-01-21
Did you update grub to point to the correct drive/partition?

If not, the boot loader might be referencing the incorrect drive.  If it says (hd0,1) and that is the primary SSD drive then it will boot that drive.  However, if the USB drive is say (hd2,1) then that's what grub needs to point to.

---

### Post by Betelgeuse on 2009-01-21
> **fatbotgw said:**
> Did you update grub to point to the correct drive/partition?

If not, the boot loader might be referencing the incorrect drive.  If it says (hd0,1) and that is the primary SSD drive then it will boot that drive.  However, if the USB drive is say (hd2,1) then that's what grub needs to point to.

How can I update grub? There is now a /boot/grub directory on my bootable usb disk. it's shown as /dev/sdd1 so should I edit the grub.conf manually or is tehere a command for this?

---

