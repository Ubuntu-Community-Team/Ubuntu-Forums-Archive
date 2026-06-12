---
title: "`can't read superblock' error when mounting usb stick"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Incompetnce on 2008-01-28
OK, there have been a few thread on related topics, none of which have helped at all. So I thought I would spell out my problem and see if anyone can help. I have a USB stick which started acting weird. So my friend helped me basically wipe it and put a fresh partition on it and then we used mkfs to put FAT32 file system on it (since the sticks purpose is to transfer files onto windows computers and back...)

we had some troubles i cant remember specifically what. but it involved guessing one of the parameters (block size?) until it worked.

eventually it did. but when i went to actually use the thing it claimed to only be 14MB or something instead of 1GB. this is a handicap.

So I decided to try putting a new file system on it. I couldn't get that to work. so I said screw it ill just put a ext3 fs on it for now until i can get some help with it. that has worked ( i think) so i dont think there is anything physically wrong with the stick. any advice?

---

### Post by Incompetnce on 2008-01-28
I spoke too soon. it didn't let me read or write to it. im trying to put fat32 on it again. here is what it says
```
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

```

thats when i try and mount it after having (apparently successfully) doing mkdosfs on it  with no options specified.

---

### Post by Earendil1982 on 2008-01-29
I'm sorry if what I'm writing is new to you. (I'm still new to all this Ubuntu stuff)
It seems to me that you did forget to use mount as superuser, as normal user you can only mount some devices  that are allowed in the /etc/fstab

Btw: add a new line to the end of your /etc/fstab
(# sudo echo >> /etc/fstab)

I'm looking for this superblock problem as well, so I can't help you there

---

### Post by rykel on 2008-06-23
Guys,

I do not know what I did, but now my 1GB thumbdrive also gives me a SuperBlock error when I insert it into Hardy. (see screenshot)

Is there a way to clean format the device and thus reset it, like we can do so with hard disks?

Thanks for reading.

---

