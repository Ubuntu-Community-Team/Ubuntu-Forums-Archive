---
title: "mint on external hdd - grub error 21"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by jhob on 2009-05-22
I posted this over at the mint forums but haven't had much of a response so I thought I would try this community here.  I'm pretty sure that my issues aren't mint specific and seeing as mint is built on ubuntu I hope it's ok for me to post this here.

I'm having a right mare trying to get mint 6 felicia to boot from my external hdd.  To install I unplugged my 2 internal disks, booted the liveCD, unmounted the external usb hdd and then ran the install with guided partition.  All installed fine but when it comes to booting I get grub error 21.

I've been trying various things after googling around for the last couple of days but nothing has worked, this has included editing menu.lst and running super grub as well as a couple of reinstalls.  

When I run super grub, go to the console and type
```
root (
```
and then hit tab it says ```
possible disks are fd0 cd
```

which seems to suggest that my external disk hasn't been found at all, which is odd as it shows up in the bios and for grub to even start it must have found the disk with grub on it so I'm rather confused as to what is going on.

On the live cd if I use fdisk -l it says 'cannot open /dev/sda', not sure if that is at all significant.

The disk has three partitions - 
dev/sda1 - ext3,
dev/sda2 - extended, 
dev/sda5 - linux-swap

If I turn the usb disk on and off while booted into the live CD it comes back up as sdd, could that be significant?

I feel totally stuck now as I've not even managed to advance the problem and I would really appreciate some help or pointers.  I'm a total linux noob and have got as far as can with this one on my own.

Many thanks

---

