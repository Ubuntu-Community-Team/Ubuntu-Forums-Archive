---
title: "moving an Ubuntu installation to another physical drive?"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by billdoor on 2006-02-15
I currently have a fairly standard Kubuntu install (root partition, boot partition, swap partition) sharing space on a drive that also has Windows XP on it. I want to move it to a different physical drive.

So far I've done this:
- repartitioned the new drive to have the root, boot and swap partitions
- used cp -a to copy every folder except for boot, dev, proc, sys and media over to my new root partition
- used cp -a to copy everything from my boot partition over to the new boot partition
- manually created new mount points in /media on the new drive
- edited fstab on the new root partition to reflect changes in partition placement
- TODO: edit the grub menu on the new boot parition and set up the mbr on the new drive

My question really is what else do I have to do? Should I just create empty /dev /sys and /proc directories on the new root parition or do I need to do something more? (Or do I not even need to do this?)

Are there any problems I could run into when simply copying everything over like this? Is there a better way?

Thanks in advance. :)

---

### Post by kwaanens on 2006-02-15
I found an easier way like this:
- make the new partition ready
- boot with Ubuntu live CD and copy the partition with gparted.
- Reboot, manually start with the new partition.
- Check fstab if anything else needs fixing, also fix /boot/grub/menu.lst
- Reboot again, just to be sure
- Delete old partition, and hold breath :)

I had one slight issue, and that was that I had to set up my ATI x300 graphics card again. Don't really know why, but it was an easy fix.

- Ketil

---

### Post by billdoor on 2006-02-15
Just switch my BIOS boot device settings and tested mine... it's kind of ok, but I hit a slight gotcha.

While hda (old ubuntu + xp install) and hdb (new ubuntu copy) remain constant regardless of which drive is used to boot, it seems like GRUB's hd0 and hd1 are switched when you change the boot device. I was assuming my new HD would be hd1 since the old one was hd0 but in fact that doesn't seem to be the case. So, I just switch all my hd1 changes back to hd0 in menu.lst and everything's ok, except...

I can no longer boot to my XP install (on hda) via the grub menu. I changed it to (hd1,0) considering that hdb is now hd0, but GRUB just hands when I try to use it. Strange :o

Also, err, I'm wondering if dpkg is going to stomp my menu.lst changes whenever it installs a new kernel? :???: Have you found that to be the case, kwaanens?

---

