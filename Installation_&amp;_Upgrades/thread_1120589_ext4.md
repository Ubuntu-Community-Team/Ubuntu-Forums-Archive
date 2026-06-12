---
title: "ext4"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by jayanramesh on 2009-04-09
Dear friends,
Is it possible to change from ext3 to ext4 in jaunty? and please tell me how? if it is possible.
Thanks

---

### Post by Partyboi2 on 2009-04-09
Yes it is, [[COLOR=Blue]this[/COLOR]]("http://smartgeeks.co.cc/wp/archives/199") is the guide I used.

---

### Post by jayanramesh on 2009-04-09
Thank you so much Partyboi2.Love to see you again.

---

### Post by whoop on 2009-04-09
This is what I did:

Booted jaunty live-cd on a system running jaunty and ext3 (on /dev/sda1 in my case), opened a terminal:

```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```

In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes).

The distribution upgrade does not seem to install the new grub stage. So I did the following to refresh grub (again from a live-cd):

```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```

---

### Post by jayanramesh on 2009-04-10
Dear Whoop,
So much,thank you so much.Great!I've done it.

---

