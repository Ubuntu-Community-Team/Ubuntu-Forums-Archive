---
title: "Hiding a partition"
date: 2009-12-20
forum: Hardware
---

### Post by nomadluap on 2009-12-20
Hello all. I just bought an Acer 5738 with Windows 7 preinstalled. I pulled out my karmic cd and installed ubuntu alongside Win7. Now, I have 3 different NTFS partitions on my drive, of which 2 appear in my Places menu: one called ACER and another, the drive in question, SYSTEM RESERVED. SYSTEM RESERVED has no important files on it, except for the win7 loader. My question is: How do I hide this drive (/dev/sda2) so that it doesn't appear in the places menu or the computer window


It will be much appreciated if I had this anwsered.:)

---

### Post by IcarusR on 2009-12-20
Install gparted, if not already installed, run from terminal
```
sudo gparted
```
right click partition to be hidden
select 'manage flags'
& select 'hidden'
Job done.

Be careful with gparted, you can mess things up with it.

---

### Post by nomadluap on 2009-12-20
> **IcarusR said:**
> Install gparted, if not already installed, run from terminal
```
sudo gparted
```
right click partition to be hidden
select 'manage flags'
& select 'hidden'
Job done.

Be careful with gparted, you can mess things up with it.

if I do this, though, will the partition still show up in GRUB?

I mean, will I still be able to boot into win7?

---

### Post by IcarusR on 2009-12-21
> if I do this, though, will the partition still show up in GRUB?

Don't know for sure, possibly not. But try it, can always change it back.

Maybe a better way of doing this would be to edit /etc/fstab & comment out the line that mounts this partition. 
This would mean that partition no longer visable from Ubuntu, but should still show in grub menu.

---

### Post by nomadluap on 2009-12-21
Thanks, IcarusR, the gparted solution worked just fine. :popcorn:

---

