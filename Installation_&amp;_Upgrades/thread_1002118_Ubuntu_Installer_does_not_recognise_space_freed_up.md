---
title: "Ubuntu Installer does not recognise space freed up by Vista Shrink partition"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by SiBrMan on 2008-12-04
(newbie question on 8.10 install - trying to install as dual boot with Vista pre-installed on a brand new Dell 1525)

Following all the advice I have read, I used Vista to shrink the C: partition to make space for Ubuntu. This seemed to go without problems and there is now unallocated space.

But the 8.10 Ubuntu Installer ("Prepare Disk Space", screen 4/7) does not recognise the space freed up by shrinking the C: partition in Vista. 
The option "Guided - use the largest continuous free space." just selects 100% of the entire disk, so I assume it would overwrite the existing partitions. Seem to be no controls to alter this.
The last option (Manual) doesn't offer me any controls to select anything other than 100% of the entire disk. 
The first option (Guided - repartition) allows me to repartition the already shrunk C: partition, and there are controls to allow me to choose the split, but if I wanted to do that, why would I have pre-shrunk it in Vista? - I still can't use the free space left when I shrunk it in Vista.
The only option which seems to do what I would expect is: "Guided - use the entire disk". (which is not what I want)
None of the options presented do what I want, which is to use the space Vista kindly freed up for me.

So why is this? Is it something to do with the two small partitions Dell have put on the disk - one at each end - maybe confusing Ubuntu installer into thinking that the entire disk is empty? (newbie question).

Would 8.04 behave in the same way?

any help much appreciated!
(as you can guess I never progressed beyond screen 4/7 because I didn't want to overwrite Vista).

---

### Post by taurus on 2008-12-04
Boot with the LiveCD and use gparted (System -> Administration) and create a partition with that unallocated space.  Then, format it to ext3.  Now, see if the installer recognizes that new partition this time.

---

### Post by jerrykenny on 2008-12-04
Alternately use the Vista disk management to create partitions for you . . . . . hopefully then Windows cant have any excuse for not booting or complaining about the partition table

---

### Post by SiBrMan on 2008-12-05
Thanks for the advice taurus,

GParted reports It is not possible to create more than 4 primary partitions.
(I guess this is why the installer did not use the free space originally)

There is:
/dev/sda1   FAT16                109.79MB
/dev/sda2   ntfs     RECOVERY     10.00GB
/dev/sda3   ntfs     OS          187.83GB     boot
unallocated                       97.66GB
/dev/sda4   extended               2.5GB      lba
  unallocated                      1.00MB
  /dev/sda5 fat32    MEDIADIRECT   2.5GB

(The 97G unallocated was from the shrink I did in Vista)

Any advice on reorganising this lot?

---

### Post by mikechant on 2008-12-05
All you should need to do is use Gparted from the live CD to move the start of the Extended partition /dev/sda4 as far 'to the left' as possible (you can just drag it). Then all your free space (should be about 100Gb) will be in that extended partition and Ubuntu can create one or more logical partitions within it. You may need to unmount /dev/sda5 if it is mounted (right click on it in Gparted to get the unmount option).
Incidently, I'm not sure what your sda5 partition is for - I didn't get one of these on my Dell.
Wikipedia has some good articles partitions etc. work - if you want to know more start here:
[http://en.wikipedia.org/wiki/Master_Boot_Record](http://en.wikipedia.org/wiki/Master_Boot_Record)

---

### Post by theozzlives on 2008-12-05
> **mikechant said:**
> All you should need to do is use Gparted from the live CD to move the start of the Extended partition /dev/sda4 as far 'to the left' as possible (you can just drag it). Then all your free space (should be about 100Gb) will be in that extended partition and Ubuntu can create one or more logical partitions within it. You may need to unmount /dev/sda5 if it is mounted (right click on it in Gparted to get the unmount option).
Incidently, I'm not sure what your sda5 partition is for - I didn't get one of these on my Dell.
Wikipedia has some good articles partitions etc. work - if you want to know more start here:
[http://en.wikipedia.org/wiki/Master_Boot_Record](http://en.wikipedia.org/wiki/Master_Boot_Record)

I got a recovery disk on my 1525, ofcourse I got rid of Vista all together. I am now using 8.10 on it.

---

