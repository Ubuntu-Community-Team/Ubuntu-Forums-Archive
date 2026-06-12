---
title: "trouble with automount of /dev/sda1"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by LINJEinc on 2005-05-11
Hi everyone!

I'm new to Ubuntu, and have a quiestion.
In my /etc/fstab I got all my ntfs disks on automount,
every drive works fine, but not my /dev/sda1 disk.

```

[COLOR=red]/dev/sda1	/mnt/share4	ntfs	ro,user,umask=022 0 0[/COLOR]

```

only way I can make it readble for my user is to do a "mount -a"
after reboot. 

Anyone knows ho to fix this problem, so I wont have to type
"mount -a" after every reboot.

//LINJEinc

---

### Post by ruben_b on 2005-05-11
i´m having the same problem. but only with partions that are ntfs!
my usbstick works fine.

---

### Post by nt7561 on 2005-05-11
I have also the same problem with a FAT32 disk
code:
[COLOR=Red]/dev/sda1   /media/common_disk     vfat    umask=000    0    0[/COLOR]

what's wrong with that?

---

### Post by ruben_b on 2005-05-12
i found an solution. for the ntfs partition you have to type:

/dev/hda1	/mnt/win	ntfs	user,umask=0444	   0	0


and for the vaft partition you'll have to set the user option, as shown above in the ntfs example.

---

