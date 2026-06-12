---
title: "Triple Boot; XP, Backtrack, Ubuntu"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by MarkW7 on 2009-05-11
Hello, 

I am having a nightmare with this; some info;

PC - 1.7GHz, 1gig Ram, Fujisu Siemens Lifebook,
OS's; Windows XP Pro, Backtrack3, Ubuntu 8.10

I can install windows no problem on sda1 as ntfs easy as pie - i can also then install Ubuntu and ;dual boot; but then when i try to add Backtrack i run out of partition space; 4max?!
They both work fine as i have also done XP and Backtrack dual booted but i'd like triple.

I am very unsure on what i need; avaliable.
What i'd like;

sda1; Windows XP; NTFS
sda2; Ubuntu / Backtrack
sda3; Backtrack / Ubuntu
sda4; FAT32 storage partition, would only be 5gb. so i can share files between.

This then uses all my partition's allowed unless there's away round it?

As of now Backtrack uses 3 partitions.
boot loader
swap &
main install - i think [Followed off youtube tut thro terminal]

Ubuntu used 2;
Main install
Swap


I hope it is possible! :(

Thank you all for comments / everything is really welcomed.

Thank you.

---

### Post by MarkW7 on 2009-05-12
.

---

### Post by brentrubeck on 2009-05-12
You need to set up an extended partition.  Here's what you do.  
1.  Install windows first.
2.  Boot up to a live linux disc and resize and repartition the drive into the partitions you need.  You can use qtparted or gparted.  You can easily find some info about repartitioning/resizing with google.  The part you missed though is that you need to create an extended partition for the rest of the partitions.  See my fdisk table below.
3.  You might have to use fdisk from the live linux CD on some of the partitions (I don't recall exactly if it was necessary), to set a bootable flag or create the filesystem.
4.  Install the versions of linux you'd like to have, but remember which partitions you are installing on otherwise you may overwrite something.

Here is my partition table (note that sda4 is the extended partition which allows for more than 4 partitions).

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896    7  HPFS/NTFS
/dev/sda2            1568        1580      104422+  83  Linux
/dev/sda3   *        1581        3492    15358140   bf  Solaris
/dev/sda4            3493       30401   216146542+   5  Extended
/dev/sda5            3493        5520    16289878+  83  Linux
/dev/sda6            7433        7687     2048256   82  Linux swap / Solaris
/dev/sda7            5521        7432    15358108+  83  Linux
/dev/sda8            7688       30401   182450173+  83  Linux

On my system sda2 is a boot partition, sda6 is the swap memory and the other ones are a couple of linux partitions, a solaris partition and a windows partition.

---

### Post by MarkW7 on 2009-05-12
Thanks!

Do i only need one extended; should i do it on sda1.
Or install Ubuntu then do it on sda4.

Should i install Backtrack or Ubuntu after windows?

:)

---

### Post by brentrubeck on 2009-05-12
You probably want to put the extended volume on sda4.  Windows, if you install it first, will probably end up on sda1 anyway.  Also I haven't installed Backtrack so I don't know how easy it is to point to a specific partition.  However, I would think either of the other two installations would be pretty similar.  qtparted and gparted have pretty easy to use graphical interfaces so you should be able to figure out those pretty easily.  Also you might want look into putting a boot partition for /boot to mount to, it used to be pretty common place, but I think people are not bothering with it anymore.  Lastly, if you want a swap partition it will probably get the best performance if you put it somewhere in the middle of you partitions (somewhere in the middle of the disk).

---

### Post by MarkW7 on 2009-05-12
May be something like;

sda1; Windows
sda2; Backtrack / Ubuntu; Main
sda3; Shared
sda4; -Extended
sda5; Backtrack / Ubuntu; Main
sda6; Swap for Backtrack & Ubuntu Mixed

Were it says' Backtrack / Ubuntu i'm still undecided wether to go with Ubuntus boot loader; Grub or backtracks; lilo.
Then whichever is best will go last :d

I don't know if i've missed anything, what you say about a boot bit? Con do i can figure the boot menu.

---

### Post by brentrubeck on 2009-05-13
The setup looks OK.  The part about a boot flag relates to this line from my fdisk -l:

/dev/sda3   *        1581        3492    15358140   bf  Solaris

The * is the boot flag and it is essentially where the computer looks for after it has read the master boot record.  You probably will not have to mess with it.  I think the last program that you install will probably set it when it configures the boot loader.

---

### Post by MarkW7 on 2009-05-13
ok :D

Any idea which to go with as a boot loader; Grub or lilo?

---

### Post by brentrubeck on 2009-05-13
Grub has more features here's an in depth look at both:
[http://www.ibm.com/developerworks/library/l-bootload.html](http://www.ibm.com/developerworks/library/l-bootload.html)

---

### Post by MarkW7 on 2009-05-13
I think ill go with grub :)

---

### Post by MarkW7 on 2009-05-13
When i configure the extended harddrive do i have to give it a size?

---

