---
title: "deleting windows, gparted, help."
date: 2005-11-13
forum: General Help
---

### Post by sunrex on 2005-11-13
im on breezy, i use KDE, but im asking here since i use gparted lol.

anyway i deleted the windows partion. its now free space, i need to know how to transfer that space over to my linux partion (free space slot one, linux slot 2)

oh and if its not alredy gone, how do i get rid of the windows boot, on grub?

oh...and for the people who wish to know why im deleting windows..

i found out about ubuntu almost...a year ago.. but i never left windows due to the limited gaming on ubuntu, a few days ago i found out how to get counter strike source to run on wine...now its crashing couse i minimized it...any ideas on how to fix that?

anyway, now...last night, i found out i had rootkit (somthing that kills every little thing..) i found out i didint have control of taskmanager..i found out that it would hardly boot up..i found out i couldent do shit on windows...im just sitting here staring at the screen, thinking, why the hell did i reinstall windows again? i mean before i had to put up with 2 months of it shutting down on me, every minute, finnaly got it fixed...now this shit......wtf is up with this bullshit!?!

thats it...

---

### Post by peterbrowne on 2005-11-13
use
```
xterm
```
and enter in command
```
sudo nano /boot/grub/menu.lst
```
find the Windoze references should be like
```

title Windows
root (hd0,1)
kernel ?
boot

```
and add a # to the beginnning of each line in the windows reference

now save  (Ctrl+X, select yes, hit enter)  and when you reboot, grub won't reference windows

---

### Post by sunrex on 2005-11-13
thanks, i sould have just looked in grub..but i have never edited the grub before lol..

still need to know on how to make the freespace go into my other partion without making a new partion

:razz:

---

### Post by chronusdark on 2005-11-14
actually i have been looking into the same thing but i just want to make my windows partition smaller and transfer the space back to linux...but the problem is that gparted doesnt support moving partitons with ext2 filesystem... and actually i have yet to find a program that does...(PS dont mess with partition magic it totally messed up my MBR)

SO.....if anyone knows how to go about this im sure me and sunrex here would be deeply indebted

FYI here is my partition table

```
Disk geometry for /dev/hda: 0.000-57241.898 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  29999.812  primary   ntfs        boot
4      29999.812  30004.211  primary   ext2
2      30004.211  56094.147  primary   ext3
3      56094.148  57239.406  extended
5      56094.179  57239.406  logical   linux-swap
(parted)

```

---

### Post by Sendervictorius on 2005-11-14
I suppose you could create a new partition with the free space, then use LVM to create a logical volume over the lot.

---

### Post by ssam on 2005-11-14
you may need to run
```
sudo update-grub
```
for grub settings to take effect.

personally i would just format the space as ext3, and mount it as something like /music, then move all my music files out of my home folder and into it.

beware of changing partition numbers when you do this. if you create a new partition at the begining of a disk then it may increment all the partition numbers of everything else. This will probably stop you computer from booting.

check the numbers of your main partition and any that you mount in /etc/fstab. if anything in fstab changes, edit the file and set it to the new device value (the /dev/hda3 bit).

if the main partition number changes then you will need to fix it in /boot/grub/menu.lst (read all the comments in that file). and run sudo update-grub.

then i will hopefully be safe to reboot. if it doesn't boot then it can probably be rescued from a live cd, so make sure you have one handy.

---

