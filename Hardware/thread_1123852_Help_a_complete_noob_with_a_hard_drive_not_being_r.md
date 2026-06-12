---
title: "Help a complete noob with a hard drive not being recognized error"
date: 2009-04-12
forum: Hardware
---

### Post by noob123456 on 2009-04-12
Hi,

Here is my problem.  I cannot access my external hard drive on either my Ubuntu installation or windows XP installation. (it previously worked).  I would like to recover the pictures that are on this drive.  

**UBUNTU**
I am able to mount for ntfs using _mount -t ntfs-3g /dev/sdg1 /home/extdrive/_.  

When I try to see contents using ls... it says _Input/output error_

If I look in a window, it shows free space 112.2 Gigs free and 178G used... (but I can't see any of the used stuff)

I tried this testdisk app... went to the analyse mode and didn't see to find anything different than the ntfs drive... 

**Windows**
From memory, when I read disk from windows XP computer, it shows me one video I had on it only...  that is it.  

I have been using this disk for windows, ubuntu and a pvr.  It has been working properly for a while now...  Also, from what I recall... this disk used to be NTFS but I recall changing it to FAT16 or FAT32 as the PVR required it that.  If I check on the PVR, it shows all the correct file structure and everything.  

Any help would be appreciated

Btw:  this is my first post ever.  usually I'm able to find stuff by searching but I'm fairly new to linux and it hasn't been going well for this one :(.

---

### Post by taurus on 2009-04-12
If you changed it to fat32, then how come you tried to mount it as ntfs (ntfs-3g)?

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by noob123456 on 2009-04-12
sudo fdisk -l gave this

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x129829db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       38913   312367860   8e  Linux LVM

Disk /dev/sdb: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cdb4dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1164     9349798+  83  Linux
/dev/sdb2            1165        1222      465885    5  Extended
/dev/sdb5            1165        1222      465853+  82  Linux swap / Solaris

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52dcc621

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       38914   312568832    7  HPFS/NTFS

df -h gave
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             8.9G  3.0G  5.5G  36% /
varrun                950M  108K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   80K  950M   1% /dev
devshm                950M  136K  950M   1% /dev/shm
lrm                   950M   39M  911M   5% /lib/modules/2.6.24-23-generic/volatile
/dev/sdg1             299G  180G  119G  61% /media/New Volume
/dev/sdh1             299G  180G  119G  61% /media/New Volume_


Thanks taurus :)

---

### Post by noob123456 on 2009-04-12
Sorry, forgot to answer the qustion.  I initially tried to mount as a fat... Couldn't get it to work.  I used gparted as suggested by my research... It showed it as ntfs so I tried that.

---

### Post by taurus on 2009-04-12
> **noob123456 said:**
> 
Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52dcc621

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       38914   312568832    7  HPFS/NTFS

df -h gave
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             8.9G  3.0G  5.5G  36% /
varrun                950M  108K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   80K  950M   1% /dev
devshm                950M  136K  950M   1% /dev/shm
lrm                   950M   39M  911M   5% /lib/modules/2.6.24-23-generic/volatile
[B][COLOR="Blue"]/dev/sdg1             299G  180G  119G  61% /media/New Volume
/dev/sdh1             299G  180G  119G  61% /media/New Volume_[/COLOR][/B]

Thanks taurus :)

Looks to me like both /dev/sdg1 & /dev/sdh1 are the same drive.

```
ls -la /media/"New Volume_"
```

---

### Post by noob123456 on 2009-04-13
ls -la /media/"New Volume_"
ls: reading directory /media/New Volume_: Input/output error
total 0

I turned off the drive earlier and when I plugged it back, it automatically detected the usb and opened up the new volume window (not sure if me fiddling around with mounting etc may have for some reason allowed it to be detected now).  Looks like I have the same problem though.

---

### Post by noob123456 on 2009-04-14
Any other suggestions or info folks need to help troubleshoot?  Still can't read the info that is on the drive.

---

