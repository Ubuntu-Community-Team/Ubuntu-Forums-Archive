---
title: "Wiped and re-installed Fully Encrypted System. Now Grub can't mount it."
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by u-slayer on 2009-06-17
Okay, so I was getting some I/O sector errors and decided to run a badblocks -vw for a few hours on my HDD.

After that I attempted to restore my system from the backup I had created earlier.

I created a new partition for the root filesystem.
Encrypted it with cryptSetup luksFormat /dev/sda1
Opened it with CryptSetup luksOpen /dev/sda1 crypto
Created the ext4 filesystem with mkfs -t ext4 crypto
Then I untarred my all the root files to the new filesystem.
Finally I used luksDump to get the new UUID and change the old one of my menu.lst file that the Ubuntu Alternate installer had created earlier on my usb drive.

Now when I try to boot from GRUB, it says:

```
Boot from (hd2,0) crypto_LUKS <UUID>
Error 17: Cannot mount selected partition
```

So grub is successfully finding my LUKS partition, It just doesn't know what do with it. Where did I go wrong?

---

### Post by u-slayer on 2009-06-17
When I change, the UUID number to the wrong one, I get a different error, So I know that GRUB is definitely finding the partition. It just doesn't know what to do with it. 

I can't imagine, how the encrypted partition I created with the alternate CD would be any different than the one, I created with cryptsetup luksFormat.

---

### Post by u-slayer on 2009-06-17
Bump, for greater victory.

---

