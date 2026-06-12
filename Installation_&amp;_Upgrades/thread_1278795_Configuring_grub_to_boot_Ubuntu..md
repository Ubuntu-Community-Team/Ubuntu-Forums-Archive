---
title: "Configuring grub to boot Ubuntu."
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by OrionFyre on 2009-09-30
Scratching my brain here as to what I'm doing wrong.

On my system I have Arch Linux. I also wanted Ubuntu so I went through practically four hours of juggling partitions so I can get Ubuntu to it's own. 

I went through and installed Ubuntu to /dev/sda8, it utilizes /dev/sda5 for /home (as does arch)

everything except /home is on sda8. I chose to leave my current boot manager intact. I went through grub's menu.lst and got Arch working peachy without a problem... I choose Ubuntu and grub hollars "file not found!"

here's the grub entry. What have I done wrong?

```
# (2) Ubuntu
title  Ubuntu
root   (hd0,7)
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro rootfstype=ext4
initrd /boot/initrd.img-2.6.28-11-generic
```
:confused:

---

### Post by Warren Watts on 2009-09-30
I recently experienced similar problems with GRUB and different distros and I discovered that the drive naming conventions used by the particular kernel being booted (sda vs. hda) was the issue.  Here's a snippet from my menu.lst:
```
title           Wolvix 2.0.0 beta2
root            (hd1,0)
kernel          /boot/vmlinuz root=/dev/hdb1 ro
savedefault
boot

title           Zenwalk Gnome Edition
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro
savedefault
boot

title           Qimo 1.0
uuid            bbd5c34a-c068-40a9-be8f-4366e6a6a531
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=bbd5c34a-c068-40a9-be8f-4366e6a6a531 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

```

You can see that Wolvix expects to see **hda** and Zenwalk expects to see **sda**.  Qimo (a Xubuntu flavor) uses UUID.

You can list the UUID's of the partitions by executing ***sudo blkid***:
```
root@wolvix warren $ blkid
/dev/hda1: UUID="a258b48b-7fbc-4a35-b0eb-7de3049dd8b1" TYPE="ext3" 
/dev/hda2: UUID="bbd5c34a-c068-40a9-be8f-4366e6a6a531" TYPE="ext3" 
/dev/hdb1: UUID="5e5ff86f-7253-4dea-87b9-da64e45ada66" TYPE="ext3" 
/dev/hdb2: UUID="6904615e-af38-4093-ba95-04053c9b67d4" TYPE="swap" 

```

Using the UUID in GRUB can make things a lot easier, especially if you often move partitions around.

---

