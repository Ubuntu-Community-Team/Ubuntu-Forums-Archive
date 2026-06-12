---
title: "Cannot mount NTFS partition from /etc/fstab"
date: 2015-10-13
forum: Hardware
---

### Post by SeijiSensei on 2015-10-13
Kubuntu 14.04
Kernel: 3.16.0-49-generic

If I mount an NTFS-formatted partition from the command prompt with
```
sudo mount /dev/sdb2  /media/BigNTFS
```
the mount works fine.  If I run "mount" from the prompt I see
```

/dev/sdb2 on /media/BigNTFS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

However if I create an entry in /etc/fstab with the same parameters:
```

/dev/sdb2  /media/BigNTFS   fuseblk rw,nosuid,nodev,allow_other,blksize=4096        0 2

```
it will not mount at boot, and if I try mounting it from the command prompt with "sudo mount /media/BigNTFS" I get the "wrong fs type, etc." error message.  I don't see any additional error messages in /var/log/syslog.

Changing the fstab entry to "ntfs" or "ntfs-3g" and just "default" for parameters returns an unknown file type error.

The partition has the correct filesystem type:
```
dev/sdb2   *   882274304  2930272255  1023998976    7  HPFS/NTFS/exFAT
```

Mounting by UUID doesn't solve this problem.  Any ideas?  I assume I could mount the partition by putting the mount command in /etc/rc.local, but I'd prefer to avoid that kludge.

---

### Post by weatherman2 on 2015-10-13
I recall that you can't - always - simply copy the line from your /etc/mtab file (which is what "mount" shows) into your fstab file.  I tried that once or twice and had issues.

Sorry, I don't have access to an fstab at the moment that I use to mount an NTFS partition, but I have done it before.  I'm sure you can find the answer quickly with some web searching and a little trial-and-error.

---

### Post by yancek on 2015-10-13
> I recall that you can't - always - simply copy the line from your  /etc/mtab file (which is what "mount" shows) into your fstab file.

I'd have to agree with that.  The entries below are first from mtab then from fstab for a windows 7 partition, only root has write permissions from Linux

> /dev/sda2 /mnt/win_7 fuseblk rw,nosuid,nodev,noexec,allow_other,default_permissions,blksize=4096 0 0
/dev/sda2 /mnt/win_7 ntfs-3g auto,user,rw,umask=002 0 0

You should be able to find examples on line for the specific permissions or users you want to have access.  Another fstab example below allows only root and user bob any access to the partition from Linux.

> /dev/sdb12 /mnt/win-test ntfs-3g defaults,auto,nouser,uid=bob,rw,umask=077 0 0

---

### Post by SeijiSensei on 2015-10-14
[quote=yancek]/dev/sda2 /mnt/win_7 fuseblk rw,nosuid,nodev,noexec,allow_other,default_permiss ions,blksize=4096 0 0[/quote]
The example I gave is nearly identical to that except for "default_permissions," but I can't get the partition to mount at all.  Instead I get the catchall error from mount:
> mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



I've mounted NTFS filesystems before; it's just that the usual methods don't seem to work reliably now.  I'm wondering if the problem might have arisen from a kernel upgrade.  I see another kernel waiting in the wings; I'll give that a try.

---

### Post by yancek on 2015-10-14
> The example I gave is nearly identical to that except for  "default_permissions," but I can't get the partition to mount at all.   Instead I get the catchall error from mount

If I put that entry which I got from mtab, in the /etc/fstab file and reboot it does not mount and I get an error occurred while mounting and the press S to skip or Ctrl D.

If i use the second entry, it mount the partition and no problem booting and the partition is mounted and accessible.  If it's an ntfs partition you may need to run chkdsk?

---

