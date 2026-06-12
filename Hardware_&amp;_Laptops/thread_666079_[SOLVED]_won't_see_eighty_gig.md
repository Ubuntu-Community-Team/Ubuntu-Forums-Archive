---
title: "[SOLVED] won't see eighty gig"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by gishaust on 2008-01-13
hi everyone

I have just put in a second eighty gig hard drive  I then formatted it using
cfdisk  i delete the partition then new the used the whole eighty gig then classed 
it as a primary the wrote and quit

The problem is that I tried to load my packup up files and got three gig on it and it says that its full
what would cause this to happen

gishaust

---

### Post by taurus on 2008-01-13
Can you post the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by gishaust on 2008-01-13
thanks for the reply the answers to your question are the following,

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         743     5968116   83  Linux
/dev/sda2             744         784      329332+   5  Extended
/dev/sda5             744         784      329301   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=51fcca79-68ce-4d73-98df-2187bbeb0f30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=73a927b3-ae98-4144-a6fc-4916d926b7f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/media/data	ext3	defaults,errors=remount-ro 0


/dev/sda1             5.7G  4.0G  1.5G  74% /
varrun                125M  268K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb            125M   88K  125M   1% /proc/bus/usb
udev                  125M   88K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm

---

### Post by taurus on 2008-01-13
> **gishaust said:**
> thanks for the reply the answers to your question are the following,

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         743     5968116   83  Linux
/dev/sda2             744         784      329332+   5  Extended
/dev/sda5             744         784      329301   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[B][COLOR="Blue"]/dev/sdb1               1        9729    78148161   83  Linux
[/COLOR][/B]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=51fcca79-68ce-4d73-98df-2187bbeb0f30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=73a927b3-ae98-4144-a6fc-4916d926b7f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/media/data	ext3	defaults,errors=remount-ro 0


/dev/sda1             5.7G  4.0G  1.5G  74% /
varrun                125M  268K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb            125M   88K  125M   1% /proc/bus/usb
udev                  125M   88K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm

Hmm...  Looks like there is no /dev/hdb1.  So, edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
/dev/hdb1	/media/data	ext3	defaults,errors=remount-ro 0
```
with this one.

```
/dev/sdb1   /media/data   ext3   defaults   0   1
```
Save it and reboot.  You should see your second harddrive mounted to /media/data now.

And if you want to write to it without root privilege, you just have to change the ownership of /media/data from root to your login name.

_Assuming_ your login name is **gishaust**, run

```
sudo chown -R **gishaust**:**gishaust** /media/data
ls -la /media/data
```

---

### Post by gishaust on 2008-01-13
thanks I looked at the three times an never saw that . It works great

gishaust

---

