---
title: "dual boot"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by flowevd on 2008-12-17
hi,

i think i know what i'm doing but i thought I'd ask the experts...

i've got a bit of partitioning to do next week. i have a 160G HDD and this is how it looks:

Ubuntu Partition (120G)
Arch / partition (10G)
Arch home partition (20G)
Swap (5G)

i boot from grub configured in menu.lst on the ubuntu partition.

sadly, i need to replace ubuntu with XP for a short time, and i'm going to need all 120G of that space. if i delete the partition and make 120G of unallocated space, will i be able to safely stick XP in without toasting my arch install?

i have, of course, looked at the guides at [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm"), but they're not specific on installing before rather than after an existing linux partition.

assuming i can get XP into that space, how should i go about setting up Grub afterwards? will i need to edit my arch fstab?

thanks for any help, cries of RTFM (if accompanied by a link to TFM), etc.

---

### Post by Triple88a on 2008-12-17
You should be able to format the Ubuntu partition on its own.  Also after you are done needing all 120 gbs for the xp, you should be able to split the 120 gb partition the xp is installed in and install Ubuntu as dual boot.

If you do not know what you are doing, the least you should do is save ur other partitions to another hard drive (external perhaps)

---

### Post by caljohnsmith on 2008-12-17
Does Arch use Grub as its boot loader? If it does, once you get Windows installed successfully, you can restore Grub by following these steps:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Arch partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you run into problems.

---

