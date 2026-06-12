---
title: "Grub Error 13 booting XP"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by shiningpathb4me on 2008-12-09
I'm totally new to Ubuntu but thought I knew everything I needed to know about grub from experience with Fedora Core and Mandriva. I've spent days trying to boot XP and out of frustration tried installing grub on sda instead of sdb (hd1) where it's always been - and I demolished my XP and couldn't recover it. :( 

I reinstalled XP on /dev/sda and partitioned sdb for ubuntu, installed again.

Same problem

To boot windows all I have to do is switch the boot order in the bios. When I put my slave first in the order, I get grub and can boot ubuntu. Sooooo

Right now my bios is functioning as my boot loader and this sucks!

I have checked MD5 checksums and burned CD's until I got one that tested perfectly.

I noticed that most folks around here don't use:

map (hd0) (hd1)
map (hd1) (hd0)

so I edited my grub at boot time to add those map commands and still no luck.

This was really simple in Fedora AFTER figuring it out. Same darn program in Ubuntu and it doesn't work. Every other linux I've run I did it the same way, grub on sdb so it doesn't touch mbr of XP.

Maybe the map command I use is being overridden by something else?

TIA


P.S. It appears Ubuntu likes to hide essential system tools from the user. The network configuration GUI's don't seem to do much of anything. I still can't manually configure an ethernet adapter. I save it, reboot, and it goes right back to DHCP again. There seems to be a lot of things missing from my system administration menu. What's the point of having a GUI sound config utility that can't run the alsa-config/install w/e stuff?

:lolflag:

---

### Post by caljohnsmith on 2008-12-10
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And please identify your Windows partition. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

Also, what does your full Grub entry for Windows look like?

---

### Post by shiningpathb4me on 2008-12-14
[U]Code & Output:
[/U]
ob1@ob1-ub1:~$ sudo fdisk -lu
[sudo] password for ob1: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00006ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d92d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    58605119    29302528+   6  FAT16
/dev/sdb2        78124095   117033524    19454715    6  FAT16
/dev/sdb3       117033525   156296384    19631430    7  HPFS/NTFS
/dev/sdb4        58605120    78124094     9759487+   5  Extended
/dev/sdb5        67119633    78124094     5502231   82  Linux swap / Solaris
/dev/sdb6        58605246    67119569     4257162   83  Linux

Partition table entries are not in disk order
ob1@ob1-ub1:~$ sudo xxd -l 2 -p /dev/sda
33c0
ob1@ob1-ub1:~$ sudo xxd -l 2 -p /dev/sdb
eb48
ob1@ob1-ub1:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
05ff
ob1@ob1-ub1:~$ sudo gedit /boot.grub/menu.lst

**** cut & paste menu.lst ****

 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


That's pretty much the default windows entry as far as I can tell. All of my atempts to get XP to boot with that have been by editing the working copy at boot time (just trying different things.)

Thanks for the help. I'm still using the bios to select my OS. I had to spend a few days working on other peoples computers!



):P

---

### Post by caljohnsmith on 2008-12-14
OK, that helps clear things up quite a bit. It looks like all you need to do would be to change your menu.lst to use the following entry for Windows:
```
title       Windows XP
rootnoverify   (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
How about giving that a shot, and let me know exactly what happens when you choose the above entry from the Grub menu.

---

### Post by shiningpathb4me on 2008-12-14
Yep. thanks. I just remembered that to grub hd0 means the 1st drive in the boot order, so even though I think of hd0 as sda, to grub sda is really hd1. Then - the silly map tricks make windows thinks its first so it won't crap out. 

SOLVED! I edited the bottom of menu.lst to reflect those changes and it works perfectly.

Thanks

---

### Post by caljohnsmith on 2008-12-14
Glad to hear that worked OK; cheers and have fun with Windows and Ubuntu. :)

---

### Post by searchfgold6789 on 2010-04-21
about post #3:
I wouldn't CUT and paste your menu.lst.
cheers,
 - search

---

