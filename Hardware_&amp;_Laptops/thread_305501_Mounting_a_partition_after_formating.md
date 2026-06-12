---
title: "Mounting a partition after formating?"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by Möller on 2006-11-23
I'm dualbooting Ubuntu with WinXP, but nevermind the Win-disk.
I've installed Ubuntu to a 120 GB disk, with 3 partitions, one swap, one with Ubuntu, and one NTFS with various files. Now I formated the various files partition to ext3 with gparted and want to be able to write files to it, which I atm can not do.
I've tried to search the forums but couldn't come up with something. =/

---

### Post by taurus on 2006-11-23
Assuming it's /dev/hda3, you need to edit your /etc/fstab to include an entry for it.

```
gksudo gedit /etc/fstab
```
Then, add the following line to the end of it.

```

/dev/hda3   /media/share   ext3   defaults   0   1

```
Save it.  Then create a mount point, mount it, and change permissions so you can write to it.

```
sudo mkdir /media/share
sudo mount -a
sudo chmod 777 /media/share
```

---

### Post by Möller on 2006-11-23
Marry me.

---

### Post by taurus on 2006-11-23
> **Möller said:**
> Marry me.
Easy there, tiger!!!  8)

---

