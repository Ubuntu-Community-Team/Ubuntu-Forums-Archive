---
title: "T60 fstab help"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by scoot1212 on 2007-02-20
Hi,
I have a T60 and I am having a problem with fstab.  I have a 2nd hard drive bay that goes in place of the dvd drive.  My 2nd hard drive has 2 partitions hda1(ntfs) and hda2(ext3).
How do I get ubuntu 6.10 to switch between /dev/hda (dvd) or /dev/hda1(ntfs) and /dev/hda2?  I swap out the dvd and 2nd hard drive pretty regularly.
Thank you,
Scott

---

### Post by tgalati4 on 2007-02-20
Good question.

USB and Cardbus devices can be hot-swapped because of the hotplug daemon running in the background looking for events such as "Hey, here's a new device, I think I will scan it for you."

I'm guessing that the DVD is part of the SCSI or pci chain, which does not like hot swapping.  You can boot off of the DVD or the hard disk, but you can't switch between them (during sleep for instance) with out file system weirdness.

A work around is to buy a cheap, USB, external DVD drive, and leave the hard disks in the bay all the time.  Plug in the USB drive when needed and hotplug will detect it as a drive and assign an appropriate device setting.

Keep the internal DVD in a protective case with a Live Ubuntu CD in it at all times as a rescue disk.

Since hard drive prices are coming down, you could also get a bigger primary internal drive (200 GB) can create partitions on it for all of your favorite Linux distributions.  Keep the Windows partition small and you will have less windows problems.

Perhaps there is a BIOS setting that can assign the DVD to a different logical IDE device number.

I've run out of ideas and coffee.

Good luck,

Terry

---

### Post by scoot1212 on 2007-02-20
Thank you Terry.

I am willing to swap out the hard drive and dvd drive while powered off.  I have a 100 gig 7200 primary and a 160 gig secondary drive.  I do a lot of work with VMware which I use Ubuntu for and I use XP for a few other things.  I have a ton of ISO files that I use between windows and ubuntu.  Is there a way to have fstab look to see if /dev/hda1 and /dev/hda2 exist and if not do nothing?  Kinda like how the dvd and floppy are setup?
Thank you,
Scott

---

### Post by tgalati4 on 2007-02-20
What you want is a script that discovers /dev/hda and if it exists copy the appropriate fstab_dvd to /etc/fstab.  It means that fstab gets rewritten upon every boot.  Not a problem.  It might actually work.

A simpler method, you can set up Grub with different entries then boot the one that you need:


Caution:  Super cheesy fix proposed.  (console commands in bold)

backup your current grub menu:  **sudo cp /boot/grub/menu.lst /boot/grub/menu.bak**
edit your current menu:  **sudo nano /boot/grub/menu.lst**

Title  I've got my second drive loaded and I want to boot from it.
root (hd2,1)    (second disk, second partition--hdb2--Ubuntu I presume)
kernel        /boot/vmlinuz-2.6-15-28-386       (put in your kernel version)
initrd         /boot/initrd-2.6-15-28-386
boot

Title      I have my DVD loaded and I want to boot Windows from the internal drive.
root      (hd0,0)
makeactive
chainloader +1

Title  I have my DVD loaded and I want to boot Ubuntu off my internal drive.
root (hd0,1)        (this is the first drive, second partition)
kernel (same as above)
initrd   (same as above)
boot

You don't need savedefault because you don't want to reboot into the same mode next time.

The fstab changing script will take some work and testing because it can only operate after booting successfully to some low run level, then continue to boot to a higher run level.  Basically boot-->discover hardware-->change fstab-->reboot with new fstab.  A failure in this script could leave an unbootable system which is bad.

The grub script is safer since it relies on you to choose the correct configuration.  If you pick the wrong one, it won't boot, but then cycling the power will get you back to the grub menu to try a different mode.

Have a copy of your existing menu.lst as a reference and you will see how powerful grub really is.

---

### Post by scoot1212 on 2007-02-22
Thank you for the suggestions but it's not quite what I am looking to accomplish.
I have a 100 gig drive that I have XP and Ubuntu on, I also have a 160 gig drive that I have files and vmware images which I use/share between XP and Ubuntu.  I would like to find a way to have fstab automatically recognize if I have my dvd drive or the 160 gig hard drive in the bay and mount them accordingly.  I am not sure if this is possible or not.
Thanks,
Scott

---

