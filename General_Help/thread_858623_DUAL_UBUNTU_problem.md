---
title: "DUAL UBUNTU problem"
date: 2008-07-13
forum: General Help
---

### Post by jnw222 on 2008-07-13
i recently used gparted to make another ubuntu install and i wanted to verify that the new install works before i delete the old one

but now any time i try to boot the new one it just goes to the old one

---

### Post by fedex1993 on 2008-07-14
It sounds like grubb is confused between the two installs.

---

### Post by overdrank on 2008-07-14
> **jnw222 said:**
> i recently used gparted to make another ubuntu install and i wanted to verify that the new install works before i delete the old one

but now any time i try to boot the new one it just goes to the old one

Also to add to fedex1993 if you had a separate home it will use all of you settings in the new install.

---

### Post by dentaku65 on 2008-07-14
You can use SuperGrubDisk to recover the Grub boot
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
It's a live cd

---

### Post by jnw222 on 2008-07-14
i figured the problem but i need help fixing it

the partition is about 40G and ubuntu, being installed on a 20G partition will not reconize the new size 

what to do now

---

### Post by jnw222 on 2008-07-14
here is a screenshot of gparted


btw both partitions really only have about 17 used gigs
but ubuntu is confused about space

btw the small ubuntu partition is mounted with no real reason

---

### Post by jnw222 on 2008-07-14
is the only doable thing to reinstall

---

### Post by Elfy on 2008-07-14
Have you reintsalled grub yet?

---

### Post by jnw222 on 2008-07-14
grub reinstalled 

new partiton (40G) bootable and functioning properly exept for the size of /dev/sda2 (new one))

---

### Post by jnw222 on 2008-07-14
and when emaning them 

under the new one the seem identical, i tried arching a the main home folder (a whopping 8G both partitions) both partions inflate identically

---

### Post by Elfy on 2008-07-14
CAn you post 

```
sudo fdisk -l
df -h
```

Can you also post your menu.lst so we can see exactly which one is booting.

```
cat /boot/grub/menu.lst
```

---

### Post by jnw222 on 2008-07-14
like they are still copying each other after the gparted copy

oh what to do

---

### Post by Elfy on 2008-07-14
Let whatever is working finish and then post

---

### Post by jnw222 on 2008-07-14
$ sudo fdisk -l
[sudo] password for USER: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2cea0b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         255     2048256   82  Linux swap / Solaris
/dev/sda2             256        6570    50725237+  83  Linux
/dev/sda3            6889        9729    22820332+   5  Extended
/dev/sda5            6889        9574    21575232   83  Linux
/dev/sda6            9575        9607      265041   82  Linux swap / Solaris
/dev/sda7            9608        9729      979933+   6  FAT16


MENU.LST in atachment

---

### Post by jnw222 on 2008-07-14
i make sure that it boots the one on hd0,1

---

### Post by Elfy on 2008-07-14
Can you post the df- h output please could you alos do 

```
sudo blkid
```

---

### Post by jnw222 on 2008-07-14
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              21G   18G  2.1G  90% /
varrun                442M  228K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   56K  442M   1% /dev
devshm                442M   12K  442M   1% /dev/shm
lrm                   442M   38M  405M   9% /lib/modules/2.6.24-18-generic/volatile
gvfs-fuse-daemon       21G   18G  2.1G  90% /home/jordan/.gvfs
/dev/sda5              21G   18G  2.1G  90% /home/lfs/Documents

---

### Post by jnw222 on 2008-07-14
sorry here is the correct menu.lst

---

### Post by jnw222 on 2008-07-14
i made a backup so  i will se what deleting the old one does

---

### Post by jnw222 on 2008-07-15
Problem Solved

---

### Post by Elfy on 2008-07-15
Hi - glad you're sorted - I had to disappear last night, sorry bout that.

What did you do to sort the problem?

---

