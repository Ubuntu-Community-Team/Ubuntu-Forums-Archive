---
title: "Weird problem with 2nd HDD changing it's device name"
date: 2008-11-19
forum: General Help
---

### Post by pollywog on 2008-11-19
I've recently upgraded to Hardy, and since then my second hard internal drive, which I use for data storage, keeps changing it's device name (i.e.sda1, sdb1). This causes it to no longer be automatically mounted, as it has always been in the past, via my fstab edit

```
#Mount Point for 2nd hard drive
/dev/sda1 	/media/Vault 	ext3 	defaults 0 	0
```

My current fdisk -l output is

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401   83  Linux

```

I'll change it again, but obviously something is amiss. Any ideas?

---

### Post by sedawk on 2008-11-19
1) You can save output from dmesg for some further debugging, e.g. to
   see which devices are assigned to /dev/sdX
2) Check which device is at /dev/sda, /dev/sdb, /dev/sdc, etc. and what
   exactly is wrong when the sorting order is "broken".
   Did /dev/sda and /dev/sdb simply swap, or are there more devices
   than before?
3) Do you sometimes connect USB memory sticks or cards into 
   a card reader. This might mess up drive sorting.
4) You might want to have a look at the whole "udev" stuff, e.g. one
   thing you can do is to change the assignment of device files.


Bye

---

### Post by taurus on 2008-11-19
You can replace the /dev/sda1 in /etc/fstab with the UUID.

```
sudo blkid
```

---

### Post by pollywog on 2008-11-19
I changed the fstab edit to use the UUID. Worked like a charm-Thanks

---

