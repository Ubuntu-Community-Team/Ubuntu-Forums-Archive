---
title: "Installing grub with a multiboot system."
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2008-12-16
This may sound like an odd question.

I have a dual-boot with Vista/Ubuntu, and I've set aside two 15GB partitions of empty space to test other OS's.

Current, I have:
sda1 - NTFS - Vista
sda2 - ext3 - Ubuntu
sda3 - ext3 - blank
sda4 - ext3 - blank

However, I've noticed in the past that whenever I install another OS (say, Ubuntu Ultimate Edition) then the OS installs a new GRUB on it's own partition, and when I boot, the system uses that.

It seems daft to have three GRUBs sat around my computer (two being redundant) so I was wondering how to stop this.  Can I simply ask each of my installers to set sda2 as /boot?  Or will this format the partition?

---

### Post by lewisskinner on 2008-12-17
Can no one help me on this?  I really don't want to have GRUB installed all over the place!

---

### Post by lewisskinner on 2008-12-17
OK, so what about the "advanced options" of the Ubuntu installation?

Can I select the same partition from every installation, and if so which partition is better?  Can it go on my Windows Partition?

---

### Post by meierfra. on 2008-12-17
> Can it go on my Windows Partition?

No, that will make Windows unbootable.

---

### Post by olivine on 2008-12-17
A good option is to make a dedicated grub partition, as described here:
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

Basically, you set up a separate grub partition during your first linux install. During later installs, you install Grub to the MBR (will be temporary), then mount the grub partition, overwrite + edit the menu.lst file to have all OSs listed there, and run grub.

It has worked perfectly for me several times (using alternate CD). Just be careful when following the instructions.

---

