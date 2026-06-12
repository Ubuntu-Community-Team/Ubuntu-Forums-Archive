---
title: "how to install ubuntu 8.10(overwrite ubuntu 5.10)"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by adameye on 2009-01-21
I'm using a CD to install 8.10 on my computer, my computer already has windows and ubuntu 5.10, I 'm trying to overwrite 5.10, I'm a little confused by the following step:

    from manual--->prepare partitions:
   device   type  mount point format? size   used
/dev/sda
/dev/sda1  ntfs                      10487MB  9377MB
/dev/sda5 fat32                      18441MB  9361MB
free space                           18441MB
/devsds6   swqp                       584MB    0MB
I think I deleted ubuntu 5.10(the free space from), but when I try to set up a new partition from free space, it looks still include used space(only part of 18441MB available)!why?
  another small question is: how to set up "used as (FAT32....)" and "mount point", thanks

---

### Post by Partyboi2 on 2009-01-21
From the free space create a ext3 partition with the mount point set as /
Ubuntu uses ext as its native filesystem, I don't think you will be able to install Ubuntu onto a fat32 partition.

---

### Post by logos34 on 2009-01-21
> **adameye said:**
> but when I try to set up a new partition from free space, it looks still include used space(only part of 18441MB available)!why?


if you can't seem to do what partyboi explained, quit the installer and go back to the live cd desktop, >System>admin>partition editor and reformat the ~18 gb as ext3 logical partition.  Run the installer again and point it to that partition to use as /

---

### Post by adameye on 2009-01-22
that worked, thank you very much
> **logos34 said:**
> if you can't seem to do what partyboi explained, quit the installer and go back to the live cd desktop, >System>admin>partition editor and reformat the ~18 gb as ext3 logical partition.  Run the installer again and point it to that partition to use as /

---

