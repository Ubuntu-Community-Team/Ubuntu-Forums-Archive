---
title: "slow ssd filesystem, install options"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by alanwalterthomas on 2009-05-06
I've spent a good couple hours reading as many evaluations of filesystems as I could but have found very little about the best ubuntu filesystem for a slow MLC ssd. I'm installing 9.04 UNR on the Acer Aspire One. It has a pitifully slow 16 GB ssd & I want the filesystem that will make it less of a bottleneck. Stability isn't the biggest issue here, but showing that it can be more responsive than the XP version might be. Very quick boot would be nice, but my main concern would be making the ssd less of a bottleneck during normal operation.
I had 8.10 installed with ext2 & it was TOO SLOW!
So I thought about installing with ext4, which ought to speed it up a bit.there are so many options that got me thinking...
However, I started thinking about the alternatives...
ReiserFS, FAT__ - not interested
ext3 - if you're going to journal an ext_ on a ssd why not ext4?
XFS - I read over & over it's made for really big files - not for a netbook.
JFS - I decided to go with this one for the main partition after reading this:
[http://dismantle-it.blogspot.com/2008_12_01_archive.html](http://dismantle-it.blogspot.com/2008_12_01_archive.html)
There it seemed to be quick & also extend the battery life. 16 GB is still pretty small & I read JFS wastes less space than ext3 (& I guess ext4). It's a journaling filesystem, which ought to help if there's a data corruption problem or ? someday, but I read somewhere that its journaling involves fewer writes than ext3 to help the ssd's life. I read it tends to fragment but fragmentation doesn't bother a ssd. Also, it uses less of the atom's limited CPU power than most filesystems. The only problem I really encountered was that IBM isn't devoting significant resources to it anymore & it's not so well maintained - how much of a problem will that be?

I'm far from being an expert; was I right in doing the following?

/ JFS 13.6 GB
(for the advantages cited above)

/boot  ext4 70.6 MB
(because I heard boot time improved dramatically with ext4 & I shouldn't have to worry about too many writes in /boot

& just a few final install questions...
1) I have 1 GB ram. As long as I don't use all the ram, I should be able to hibernate with this 1.4 GB swap right?
2) I set the / JFS partition as primary & boot & swap as logical. Is that okay?
3) I installed 9.04 using the automatic use all disk option, the found out later that the swap partition /dev/sda5 was encased in an extended (what's extended?) partition /dev/sda2. Doing it manually, I don't get that. Does it matter?

---

### Post by alanwalterthomas on 2009-06-11
no insightful replies...?

I set up the following too:

Edit /etc/fstab
After the hard drive, change defaults to defaults,noatime,nodiratime

Edit /boot/grub/menu.lst
Add elevator=deadline to the kernel line.

I also put firefox's cache into a ramdisk.

It seems to have helped a bit.

Any more suggestions, let me know.

---

### Post by slidersv on 2009-07-14
> **alanwalterthomas said:**
> no insightful replies...?

I set up the following too:

Edit /etc/fstab
After the hard drive, change defaults to defaults,noatime,nodiratime

Edit /boot/grub/menu.lst
Add elevator=deadline to the kernel line.

I also put firefox's cache into a ramdisk.

It seems to have helped a bit.

Any more suggestions, let me know.

How did it go? Did you install it?

---

### Post by alanwalterthomas on 2009-09-25
I suffered with the AAO's pathetically slow 16GB ssd for a few months. I avoided using it mostly.
I just installed 9.10 alpha 6 with ext4 & out of the box it's much better & more responsive, even if it isn't going to win any contests.
Don't bother with JFS on a slow ssd.

---

