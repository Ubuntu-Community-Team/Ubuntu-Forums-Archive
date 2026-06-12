---
title: "Upgraded Hard Drive, Old Partition Size Remains"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by Trite on 2008-01-02
When I built my Ubuntu Server system, the 40GB drive I was going to use failed during the build. So I substituted it with a 2GB SCSI drive I had in the junk drawer.

A few days ago I swapped the 2GB drive with a 40GB. I built the partition table under windows using Partition Magic. 2GB swap partition, rest (~37GB) went to a EXT3 partition. I used Ghost to clone both partitions and installed the hard drive.

Everything booted up fine, but my main partition is still showing as 1.9GB which isn't quite how the drive is really partitioned.

fdisk -l
```
Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4721    37921401   83  Linux
/dev/hdb2            4722        4982     2096482+   f  W95 Ext'd (LBA)
/dev/hdb5            4722        4982     2096451   82  Linux swap / Solaris

```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             1.9G  666M  1.1G  38% /
varrun                189M   60K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   48K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm

```

Obviously I'd prefer to resolve this without reformatting, or altering the partition table.

Thanks.

---

### Post by kidders on 2008-01-04
Hi there,

It seems like you dumped a 1.9GiB filesystem onto a 36.2GiB partition. Partition & filesystem sizes are independent of one another ... you've essentially put a small thing in a great big box.

You'll need to resize your filesystem to take up all the space available in the partition it occupies. Personally though, I would avoid an on-the-fly resize procedure at all costs. Instead, to minimise the possibility of screw-ups, I would suggest ...
[LIST=1]
[*]Boot your computer using a LiveCD ... or anything other than the hard disk you want to alter.
[*]Create a temporary filesystem somewhere, at least 666MiB in size. Temporarily deleting your swap space & replacing it with an Ext2 filesystem would do the trick.
[*]Copy (eg cp -dpR) the contents of the midget filesystem to the temporary location.
[*]Recreate (eg with mkfs) the filesystem at hdb1. Be sure mkfs tells you this one is about 36GiB in size.
[*]Throw the original contents (with cp -dpR again) back where they belong.
[*]If you used your swap space like I suggested, recreate it too, and check that your /etc/fstab is still consistent ... ie that it doesn't contain a reference to your swap's previous UUID.
[*]Reboot.[/LIST]This way is a bit more long-winded than opening a filesystem resizer and pressing "Go", but it's *miles* safer, and comes with the added benefit of defragmenting your filesystem. Essentially, the distinction is between doctoring the filesystem you already have so it's *waaaay* bigger than originally intended, and creating a nice clean one to take its place.

---

