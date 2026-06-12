---
title: "Problem formatting on Asus eee 901"
date: 2009-02-24
forum: Hardware
---

### Post by simocusi on 2009-02-24
hey,

I have an Asus eee901 and had XP on the 4gb HD and Ubuntu on the 16gb HD. Ubuntu crashed since I kept accepting all updating proposals and then I (stupid me) manually erased the 16gb partitions from winXP in order to reinstall Ubuntu.

Then neither XP nor the live Ubuntu could detect the 16gb HD. I used Testdisk to recover the partitions and here they are again!

Now I have installed ubuntu on the 4gb HD and am trying to format my injured 16gb HD using Gparted but no way. Tried ext3, swap,nfts,... Gparted displays an exclamation icon next to the partition name and as filesystem says Unknown.

I wonder if the HD is lost..for ever. Any idea of how to get the HD formatted and ready to install ubuntu on it again?

thanks

---

### Post by 67comet on 2009-02-24
If you've got Ubuntu already installed try using fdisk and mkfs to format it.

In CLI (terminal) type:
sudo fdisk -l
This will show you all your partitions/drives etc.

If they look fine, then write down or remember which partition is your 16gig portion (should be like /dev/sda1 or /dev/sdb1 .. fdisk will show you). Depending on what you want to partition it as type:
sudo mkfs.fat /dev/sdb1 (what ever fdisk said your 16Gb was) for fat32 or mkfs.ext3 /dev/sdb1 for ext3 .. you can hit tab twice after mkfs. to see what your choices are ..

Once it is partitioned and formated you'll need to tell Ubuntu about it in /etc/fstab.

Hope this helps.

---

### Post by simocusi on 2009-02-25
thanks

I could fix it using: shred -n 1 -f -v dev/sdb

This wiped my HD and then I could install Ubuntu again on it. For now it works fine.

simocusi

---

