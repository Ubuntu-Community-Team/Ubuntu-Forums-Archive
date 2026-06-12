---
title: "Partition Help"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by rmadhu on 2009-02-11
Hi all ,
  I need a help in partitioning  as I move from Windows to Ubuntu . 

My Initial Set up was 

  /dev/sda1   ntfs               Windows C:   10Gb
 /dev/sda2   extended 
   /dev/sda5  ntfs               Windows D:    10 Gb
   /dev/sda6  ntfs               Windows E:    9 Gb
   /dev/sda7  ext3               linux        10 Gb
   /dev/sda8  ext3               Linux Swap    1 Gb


I found that ubuntu was good and move out of Windows and I want a 
separate partition for /home and for installation of other s/w so that 
whenever I upgrade ubuntu my default home remains same and my s/w
installations remains untouched . I want to do this without losing data . 

I want the setup something like this 

Partition 1  Softwares  /15 Gb
Partition 2 /home        /14 Gb
Partition 3 / ubuntu      10 Gb
Partition 4 linux swap space 1 Gb 

As I already have ubuntu installed , I want to retain the linux and its swap space and format other 2 partitions and make it available for ubuntu . 

I tried using Gparted  and partly partitioned . Now my partition looks like this 
 /dev/sda1   ntfs               Windows C:   10Gb
 /dev/sda2   extended 
   /dev/sda5  ntfs               Windows D:    10 Gb
   /dev/sda6  ext3                             9 Gb
   /dev/sda7  ext3               linux         10 Gb
   /dev/sda8  ext3               Linux Swap    1 Gb

Can you pl explain how do I go abt acheving my intended configuration using Gparted.

Thanks,
Madhu

---

### Post by x33a on 2009-02-11
could you please post a screenshot of your gparted window.

---

### Post by Mark Phelps on 2009-02-12
Last time I tried, GParted would not let me move a partition inside an extended partition outside of it -- which is essentially what you're trying to do.

I think what you will have to do is back off your partitions, reformat your drive with the setup you want, and then restore the partition data from backup.

You should be able to do all of that using "dd" -- but I don't use that enough to remember the specifics.

Even then, the order of partitions will be different, so files like /boot/grub/menu.lst and /etc/fstab (where they refer to the partitions using /dev/sda instead of UUID) will have to be edited before you can boot back into Ubuntu.

---

