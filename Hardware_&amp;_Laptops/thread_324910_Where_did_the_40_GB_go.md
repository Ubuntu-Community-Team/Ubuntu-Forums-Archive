---
title: "Where did the 40 GB go?"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by pickarooney on 2006-12-24
Right, I have a 200GB secondary hard drive, called /dev/hdb. It was partitioned into two pieces, a 160GB and a 40GB piece (give or take). Not having any real use for the 40GB partition, and being over 95% full on the 160GB, I decided to amalgamate them into one. So, I unmounted the drive and ran gparted, then deleted the smaller partition and expanded the larger one to fill the entire disk. Although the system crashed shortly afterwards, according to gparted the expansion worked. When I consult the gparted interface it shows me a 200GB partition at hdb1 (actually 189GB, but who's counting). It also tells me that I'm using 175GB of space on it, and that it's 95% full.
When I run qtparted, it also tells me I have a 189GB partition on /dev/hdb1, but according to it I'm only using 137GB of it.
When I type **df -kh .** it tells me that the partition is only 145GB with 131GB in use.
I've run e2fsk, unmounted and remounted, using both the fstab file and manually mounting, rebooted, and the situation stays the same. I have three different programs giving me three conflicting opinions on how big and full my HD is.

I've lost 40GB, I'm still very low on space and now don't even have an extra partition to stock files one. What on earth is going on and how do I get my space back?

---

### Post by taurus on 2006-12-24
What's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by pickarooney on 2006-12-24
Like so:
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         127     1020096   83  Linux
/dev/sda2           23948       24321     3004155    5  Extended
/dev/sda3             128        5226    40957717+  83  Linux
/dev/sda4            5227       23947   150376432+  83  Linux
/dev/sda5           23948       24321     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9729    78148161    5  Extended
/dev/hda5             702         732      248976   82  Linux swap / Solaris
/dev/hda6             733        9729    72268371   83  Linux
/dev/hda7               1         701     5630688   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24792   199141708+  83  Linux

```

---

### Post by taurus on 2006-12-24
And what does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by pickarooney on 2006-12-24
thusly:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=23cd75dd-8522-4cc8-8026-43d34facd54f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=38771644-df5d-4863-95ef-4abcf0a9c696 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=6aca9cac-5354-4183-bf88-68e9e62bed9a /home           ext3    defaults        0       2
# /dev/hda6
UUID=f3466d96-c519-11d7-9a37-a027fa319c88 /media/oldhome  ext3    defaults        0       2
# /dev/hda7
UUID=bb8c5418-a024-4cc0-a287-4b1b083042af /media/oldsystem ext3    defaults        0       2
# /dev/hdb1
UUID=f084d777-e5ba-49df-b71b-729b2c0d2475 /media/supersize ext3    defaults        0       2
# /dev/sda5
UUID=7db0edf9-d00d-4b15-a5c3-c738a9091488 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2006-12-24
When you merge or reformat a partition, the UUID would change.  Therefore, modify your /etc/fstab, replacing this line

```

UUID=f084d777-e5ba-49df-b71b-729b2c0d2475 /media/supersize ext3    defaults      0       2

```
with this one.
```

/dev/hdb1   /media/supersize   ext3   defaults   0   2

```
Reboot and see what happens?

```
df -h
```

---

### Post by pickarooney on 2006-12-24
Same result:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              39G  4.5G   32G  13% /
varrun                502M   84K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  180K  9.9M   2% /proc/bus/usb
udev                   10M  180K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M  7.4M  495M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1             934M   26M  859M   3% /boot
/dev/sda4             142G   93G   42G  70% /home
/dev/hda6              68G   56G   13G  82% /media/oldhome
/dev/hda7             5.3G  3.1G  2.0G  61% /media/oldsystem
/dev/hdb1             145G  131G  7.2G  95% /media/supersize
/dev/hdd              4.4G  4.4G     0 100% /media/cdrom0

```

---

### Post by pickarooney on 2006-12-25
Found it (with a little help). I needed to resize the filesystem along with the partition with
resize2fs -p /dev/hdb1

---

