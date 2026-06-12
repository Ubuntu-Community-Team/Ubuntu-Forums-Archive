---
title: "Install Question"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by doktormiod on 2009-04-19
Hi, I installed a few linux distros before but recently i've been having some probles with hard drive so I decided to ask here for some help since I have absolutely no knowledge about this stuff (partitons, logical, primary, extended and so on... :P)
About 2 months ago I formatted entire disk and installed win xp. Than problems started. In xp installer I divided disk into 2 partitions (c,d) and it wouldn't install on C(i have no idea why) so i left it unused and continued with D. Later when a tried to merge these partitions it wouldn't boot (no bootloader found or sth like this). What's interesting, windows partition(d) was intact but after installing linux grub didn't my xp :/. Eventually i formatted everything once again, and installed xp on D like i did before. Now my disk looks like that([http://img411.imageshack.us/my.php?image=beztytuu1xvw.png](http://img411.imageshack.us/my.php?image=beztytuu1xvw.png)).
I would be glad if someone could take a look and say if it's safe to install linux on C(/home) and Unallocated space (root). I have no idea what this 'extended', 'primary'... mean, maybe on some i can't install OS or sth :/. By 'safe' i mean there won't be any problems with running windows.

---

### Post by zvacet on 2009-04-19
Yes,you can install Ubuntu on the C partition.During install change format from NTFS to Ext3,because that is default Ubuntu format.Extend your D to the unallocated space.Then shrink D partition from left to right,so that unallocated space come between C and D.Then you can extend your C and then install Ubuntu.I will install it manual way so that is possible to have home on separate partition.I don´t know if you can do this things with Paragon and if you can not download [Gparted live Cd.]("http://gparted.sourceforge.net/")

---

### Post by doktormiod on 2009-04-19
Thanks for the answer, but is it fine if i will leave partition D as it is and let it be between C(home) and unallocated space(root)?
Last time i tried to merge D and unallocated space windows stopped booting :/

---

### Post by zvacet on 2009-04-19
You should be able to merge partition with unallocated space( because unallocated space is free space not a partition.).I did it with Gparted and I don´t have any experience with Paragon.About leaving partitiond as they are I think you will not have problem.reason I suggested you to merge aprtition and unallocated space is that 21GB is to much for root.But that will not hurt.In that case put home partition on C and formar both (root and home) as ext3.Small part of C you will dedicated to swap( depends of your ram but I don´t you will need more then 1-2GB).

---

### Post by doktormiod on 2009-04-19
Thanks, last time i had 23 gb for root and it was more than enough :-)

---

