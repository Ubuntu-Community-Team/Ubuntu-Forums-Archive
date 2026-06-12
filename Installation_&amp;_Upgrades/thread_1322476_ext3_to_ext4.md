---
title: "ext3 to ext4"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by groovomata on 2009-11-11
Hello all,
I've installed Koala and now I'd like to change my home partition to ext4. My setup is that I have a system partition: /dev/sda1 and an extended partition /dev/sda2 which is comprised of /home: /dev/sda5 and swap: /dev/sda6. When I originally installed Koala I decided to leave my home partition as ext3 so I wouldn't have to format it. I've backed everything up and so I'd like to change it now.

I tried to use gparted to unmount the partition but it wouldn't let me saying:
> umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

I then visited the Ext4 Howto wiki ([http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Creating_ext4_filesystems](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Creating_ext4_filesystems)), and tried to enter the following command:
```
mkfs.ext4 /dev/DEV
```
And it said correctly that:
> /dev/sda5 is mounted; will not make a filesystem here!
My question is how can I unmount my ext3 'home' partition. Secondly how do I change it into an ext4 'home' partition.
Thank you,
Erik.

---

### Post by mikewhatever on 2009-11-11
You can't unmount it as long as it is being used, which means you have to use your Karmic live cd. Partitions aren't mounted when booting from a live cd, so that you shouldn't have that issue. I'd recommend packing up your files first.

---

### Post by groovomata on 2009-11-11
I ended up doing a reinstall. I tried to run through the install setup without formatting my system partition, but it threw up an error message suggesting that my symlinks and mount points would get screwed up. So I thought for the extra 30 minutes or so it would take to add and tweak it was not worth it.
Thank you though.
Erik.

---

