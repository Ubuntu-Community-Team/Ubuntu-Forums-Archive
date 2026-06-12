---
title: "Clonezilla &amp; New HDD"
date: 2011-01-13
forum: Hardware
---

### Post by iCeD00D on 2011-01-13
Good evening.  Today I installed a new 500GB HDD in my laptop.  I then used Clonezilla to clone my Ubuntu build to this drive (the old drive was 160GB).  After cloning, i then put the drive in the primary slot and booted.  Only to find out that it did an exact clone and did not 'extend' or use all of the drive.  I have over 300+GB of unused space that I'd like to use.  I installed GParted but wanted to see about extending the unused space into the primary partition (sda1).  Whats the best way to do this or best practices?  Thanks..

---

### Post by papibe on 2011-01-13
That's the way Clonzilla works. In order to use the extra space you'll need another tool. The partitions have to be unmounted in order to resize them. The best way is to boot into a live CD with gparted installed.

Good news is that the Ubuntu desktop installation CD works great because is also a live CD ("try ubuntu option"), and because it has gparted installed. If you still have it around you're all set.

Another alternative would be to create a gparted-only live CD (check [here]("http://gparted.sourceforge.net/livecd.php")).

I hope it helps.

---

### Post by aysiu on 2011-01-13
In expert mode you need to choose the -k1 option to resize the image when you restore it.

---

### Post by iCeD00D on 2011-01-14
Thanks for all the replies... I'll give that a shot ...

---

### Post by darkhelmetchris on 2011-01-14
I agree with aysui and papibe.  I have cloned hard disks for years with dd or ddrescue, and then used GParted to "stretch" the partition on the new larger drive.  This has been an excellent tool for me.  Running GParted from a LiveCD is usually my method of choice.

---

### Post by iCeD00D on 2011-01-14
Apparently I'm a tard again cause I could not do it last night.  I booted off the Ubuntu Live CD , ran gparted and selected the partition to extend.  Unfortunately it wouldn't go past it's already assigned size.  I just ended up creating a second partition, mounting it in fstab and then doing a ln -s in my home directory .. seems to work for now..

---

### Post by iCeD00D on 2011-01-14
Apparently I'm a tard again cause I could not do it last night.  I booted off the Ubuntu Live CD , ran gparted and selected the partition to extend.  Unfortunately it wouldn't go past it's already assigned size.  I just ended up creating a second partition, mounting it in fstab and then doing a ln -s in my home directory .. seems to work for now..

---

