---
title: "Hard Disk woes"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by Corgana on 2006-11-17
So I've Successfully got my second hard drive installed, and I can read and write and browse it no problemo. Only just today whilst copying some files to it, It says the hard drive is full!

:confused: 

It's a 20 Gigabyte drive, and Ubuntu recognizes that in the "Disks" menu. However, My "mount point" folder under "properties" says it's using 11gb and yet only has 600mb free. Is there some space ubuntu set aside on this drive? I'm only using it for storage.

Thanks in advance!

---

### Post by taurus on 2006-11-17
If you are using ext3, 5% will be set aside for journal.  What does this command look like from a terminal?

```
df -h
```

---

### Post by Corgana on 2006-11-17
> **taurus said:**
> If you are using ext3, 5% will be set aside for journal.  What does this command look like from a terminal?

```
df -h
```

```
/dev/hda1              37G   26G  9.3G  74% /
varrun                126M  256K  125M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M  140K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1              19G   18G  661M  97% /backup
/dev/hdb1              19G   18G  661M  97% /hdb
```

It is extended 3, But I'm definitley missing more than 5%

---

### Post by taurus on 2006-11-17
Why do you mount a same partition at two different mount points???

```

/dev/hdb1              19G   18G  661M  97% /backup
/dev/hdb1              19G   18G  661M  97% /hdb

```
What does your /etc/fstab and fdisk look like anyway?

```

cat /etc/fstab
sudo fdisk -l
```

---

### Post by Corgana on 2006-11-17
> **taurus said:**
> Why do you mount a same partition at two different mount points???

I was under the impression that I renamed the first mount point..:oops: 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /hdb            ext3    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4820    38716618+  83  Linux
/dev/hda2            4821        4865      361462+   5  Extended
/dev/hda5            4821        4865      361431   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
16 heads, 63 sectors/track, 39704 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       39704    20010784+  83  Linux

```

---

### Post by taurus on 2006-11-17
D'OH!!!

The entry for /dev/hdb1 is wrong in /etc/fstab.  It should look like this...

```

/dev/hdb1   /hdb   ext3   defaults   0   1

```
After making the change, reboot and see what happens with the output of this command from a terminal again.

```
df -h
```

---

### Post by Corgana on 2006-11-17
I hate myself for this, But it seems I didn't empty the trash..](*,) 

The trash icon looked empty, but after restart I noticed it was very full. Free space is now 7.6 gigs..
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G   26G  9.3G  74% /
varrun                126M  156K  125M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M  140K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1              19G   12G  7.3G  61% /hdb

```

I don't know If you can tell from that, but is the 5% you mentioned above free?

Thanks all the help & quick replys!

---

### Post by taurus on 2006-11-17
If you want, you can see which directory in /hdb is taking up most space with (from a terminal again)

```
sudo du /hdb
```

---

