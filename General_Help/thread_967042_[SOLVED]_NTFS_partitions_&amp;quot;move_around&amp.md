---
title: "[SOLVED] NTFS partitions &amp;quot;move around&amp;quot; from reboot to reboot"
date: 2008-11-01
forum: General Help
---

### Post by rewbs on 2008-11-01
Hi all,

Below is part of my fstab.
As you can see, I have a bunch of ntfs partitions on sda, sdb and sdc:

```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /hd/slowStore ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda6 /hd/soundApps ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda7 /hd/art ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda8 /hd/samples ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb1 /hd/fastSystem ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb6 /hd/fastApps ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc6 /hd/mediaStore ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

My problem is that often when I reboot, sda, sdb and sdc switch around. 

For example: my "sound apps" were on /dev/sda6 when I wrote up that fstab. But after a reboot, they could end up on /dev/sdb6 or /dev/sdc6.. so consequently, my sound apps might get mounted on /hd/mediaStore and my media store might get mounted on /hd/soundApps. As you can imagine, this is very annoying.

The problem is intermittent and I have not yet been able to identify a pattern. Any thoughts on how I could investigate further?

Cheers,
Robin

---

### Post by dcstar on 2008-11-01
> **rewbs said:**
> Hi all,

Below is part of my fstab.
As you can see, I have a bunch of ntfs partitions on sda, sdb and sdc:

```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /hd/slowStore ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda6 /hd/soundApps ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda7 /hd/art ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda8 /hd/samples ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb1 /hd/fastSystem ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb6 /hd/fastApps ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc6 /hd/mediaStore ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

My problem is that often when I reboot, sda, sdb and sdc switch around. 

For example: my "sound apps" were on /dev/sda6 when I wrote up that fstab. But after a reboot, they could end up on /dev/sdb6 or /dev/sdc6.. so consequently, my sound apps might get mounted on /hd/mediaStore and my media store might get mounted on /hd/soundApps. As you can imagine, this is very annoying.

The problem is intermittent and I have not yet been able to identify a pattern. Any thoughts on how I could investigate further?

Cheers,
Robin

Simply assign Volume Labels to your partitions and mount them using those labels in fstab.

---

### Post by caljohnsmith on 2008-11-01
Or if you don't want to assign labels to all your partitions, you could just use UUIDs in your fstab to mount the partitions. To see your UUIDs, you an use:
```
sudo blkid -c /dev/null
```
And then your fstab entries would look similar to:
```
#/dev/scd1:
UUID=23kjlkj442-23345lkjlk23-234lkjohoh3434 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
Then you don't have to worry about how your HDDs change order.

---

### Post by dcstar on 2008-11-01
> **caljohnsmith said:**
> Or if you don't want to assign labels to all your partitions, you could just use UUIDs in your fstab to mount the partitions. To see your UUIDs, you an use:
sudo blkid -c /dev/null
And then your fstab entries would look similar to:
```
#/dev/scd1:
UUID=23kjlkj442-23345lkjlk23-234lkjohoh3434 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
Then you don't have to worry about how your HDDs change order.

UUIDs change if you reformat partitions of change equipment, labels are far simpler to use as you only have to change the external device partition name rather than have to hack around with your fstab file if anything changes in the future.

---

