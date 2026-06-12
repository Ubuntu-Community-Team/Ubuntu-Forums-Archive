---
title: "Installation help! Anxious to get going =D"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by everyonedoesit on 2009-06-02
I'm a newbie to linux - had a play around with Ubuntu before but i've settled for Mint as my final choice for my new laptop (i understand the installation is identical, so i figured this forum would be okay)

Hardware configuration is 1 disk split into two partitions C and D (both more or less 100GB) - C is already full with windows and my games and D is empty.

I get to the partition section where i see this, and i'm not sure what to do - i want to install it on the D drive (which is SDA3 ntfs at the moment) but i don't know which options to select. I want linux to be able to take 10-20 gb of the disk but leave the rest accessible in windows if i need it.

Screenshot:

i13.photobucket.com/albums/a259/everyonedoesit/mint.jpg

What do imake the "Use as", and do i make the size what i want for linux? or would that resize the whole partition to 10gb. Confuzzled. Thanks guys :-)

(P.S that 15gb of unusable space is what i removed from vista in Disk Management like i read on a guide to do first, but that didn't work. If i can get it installed there, even better. If not i can reallocate to windows)

EDIT: And if it helps, here's my computer management from Vista

i13.photobucket.com/albums/a259/everyonedoesit/windows.jpg

---

### Post by utnubuuser on 2009-06-02
When I install a dual boot, I usually arrange the partitions with gparted **before I start the install **(it's on the live CD  under System>>Administration>>Partition Editor.

I start gParted, when the partitions are listed, I highlight the right-most partition, select "resize/move", slide it to the left until I've freed enough room for Ubuntu, (don't format, just leave it as an unused space), click apply, and let the editor resize the partition.
When done, double -click install on the desktop and at partitioning select "use largest continuous free space".

[COLOR="Red"]**WARNING:**_This applies to Windows XP installs only! _[/COLOR] WILL NOT WORK UNDER VISTA!!!
For Vista, you have to use a Vista disk to change partitions.

---

### Post by everyonedoesit on 2009-06-02
I am using vista, as stated. Thanks.. i guess =D

---

