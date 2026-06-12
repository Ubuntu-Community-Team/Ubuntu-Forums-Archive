---
title: "/var is full, but Disk Analyzer says it's not"
date: 2008-11-10
forum: General Help
---

### Post by HyperHacker on 2008-11-10
Thunar, Conky, and System Monitor all say /var is full, but when I look in the Disk Usage Analyzer to see what's taking up all that space, it only shows about 300MB used. :confused:

---

### Post by ciscosurfer on 2008-11-10
> **HyperHacker said:**
> Thunar, Conky, and System Monitor all say /var is full, but when I look in the Disk Usage Analyzer to see what's taking up all that space, it only shows about 300MB used. :confused:It looks like it is full.

Edit:  Disk Usage Analyzer could also have a bug.  Check your stats in a terminal```
df -h

df -k

df -m
```

---

### Post by HyperHacker on 2008-11-11
Yes, it's definitely full. I don't know what's taking up all that space though. Is there another way to find which directories are taking up the most space?

---

### Post by taurus on 2008-11-11
```
cd /var
sudo du -h
```

---

### Post by HyperHacker on 2008-11-12
That shows the same results. 318M, mostly in /var/lib. I can move files out of it and the free space does increase, but there still seems to be about a gigabyte less space then there should be.

---

### Post by geirha on 2008-11-12
Does these two commands show a mismatch for /dev/sda5?
```

sudo fdisk -l
df -h

```

It's possible that the partition is 1.3G, but the filesystem is only 300M

---

### Post by HyperHacker on 2008-11-13
I'm not sure what the output from fdisk really means in terms of size. How big is a block?```
hyperhacker@mercury:/var$ sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aaacd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32         280     2000092+  83  Linux
/dev/sda3             281        1027     6000277+  83  Linux
/dev/sda4            1028       60801   480134655    5  Extended
/dev/sda5            1028        1214     1502046   83  Linux
/dev/sda6            1215        1463     2000061   82  Linux swap / Solaris
/dev/sda7            1464       60801   476632453+  83  Linux

hyperhacker@mercury:/var$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             1.9G  177M  1.7G  10% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  232K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  3.0M  502M   1% /dev
tmpfs                 505M     0  505M   0% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda1             228M   12M  204M   6% /boot
/dev/sda7             451G  202G  227G  48% /home
/dev/sda3             5.7G  2.8G  2.6G  53% /usr
/dev/sda5             1.5G  1.4G     0 100% /var

hyperhacker@mercury:/var$ mount
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
/dev/sda5 on /var type ext3 (rw,relatime)
```(unrelated lines from mount and fdisk removed.)

---

### Post by p_quarles on 2008-11-13
I would run a filesystem check on /dev/sda5 as soon as possible. There is definitely something seriously wrong there, and my guess is that it's corrupted somewhere.

---

### Post by HyperHacker on 2008-11-13
It just went back to normal when I rebooted. (Everything is reporting ~300MB used.) I'll do that anyway though.

---

