---
title: "disk space discrepancy"
date: 2008-08-19
forum: General Help
---

### Post by ranjeet2000 on 2008-08-19
I have a 60gb harddrive. partitioned into 20GB(for OS related stuff) and 40GB(for working files, pictures etcs)

On my 20GB, i have windows and ubuntu 8.04 installed. it says 5Gb is used of the 20GB. 

When i'm in ubuntu, the desktop has only 1.5gb available, and the administrator has 0gb.

when I try to install updates, i think this is why it can't.

why don't I have more available Hard drive space?

---

### Post by Elfy on 2008-08-19
Can you run this from a terminal

```
sudo fdisk -l
```

---

### Post by ranjeet2000 on 2008-08-19
> **forestpixie said:**
> Can you run this from a terminal

```
sudo fdisk -l
```

I got this

/dev/sda1   *           1        2553    20506941    7  HPFS/NTFS
/dev/sda2            2554        7270    37889302+   f  W95 Ext'd (LBA)
/dev/sda3            7271        7296      208845   88  Linux plaintext
/dev/sda5            2554        7270    37889271    7  HPFS/NTFS

---

### Post by Elfy on 2008-08-20
I don't recognise the filetype - is this an ordinary install or is it a wubi.

If it is wubi - you can resize the partition, but I've not done it myslef so can only show you the information
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

---

### Post by ranjeet2000 on 2008-08-20
> **forestpixie said:**
> I don't recognise the filetype - is this an ordinary install or is it a wubi.

If it is wubi - you can resize the partition, but I've not done it myslef so can only show you the information
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

i first installed windows, then installed ubuntu using the regular installer cd.

---

### Post by Elfy on 2008-08-20
Did you install from within windows - it is in the add/remove in control panel or did you boot the livecd without starting windows and install from there.


Edit - please run this from a terminal

```
df -h
cat /etc/fstab

```

---

### Post by ranjeet2000 on 2008-08-24
> **forestpixie said:**
> Did you install from within windows - it is in the add/remove in control panel or did you boot the livecd without starting windows and install from there.


Edit - please run this from a terminal

```
df -h
cat /etc/fstab

```

i booted the livecd without starting windows

i entered that into the terminal and got this

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      5.1G  4.0G  867M  83% /
varrun                252M  104K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   64K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      5.1G  4.0G  867M  83% /home/administrator/.gvfs
/dev/sdb1             233G  106G  128G  46% /media/MAGIC
administrator@administrator-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Elfy on 2008-08-24
Ok - I'm sure that's wubi and unfortunately I have no real experience with it.

---

### Post by Joeb454 on 2008-08-24
How did you install Ubuntu? Was it from within Windows?

---

### Post by Elfy on 2008-08-24
If you look at your df -h you can see that you have 

5.1G 4.0G 867M 83% /

so that shows that you have just over 1Gb left in the buntu partition you made at the beginning. The rest of the space that is the windows drive should be availabvle to you in /hosts - I think :)

I don't understand why you say the administrator has 0Gb - what command gave you that response?

Try to do an update and then post the end of it if there's an error

```
sudo apt-get update
```

---

