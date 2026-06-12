---
title: "[SOLVED] fstab and added ntfs drive"
date: 2008-12-10
forum: Hardware
---

### Post by EvilRick on 2008-12-10
Here's my fstab, I added the bit about "/dev/sdc1"

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=BA74C82874C7E4EB /winxppro       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2e28f1b0-afc0-4bac-8cfa-6c65e162340e none            swap    sw              0       0
# /dev/sdb1
UUID=1f6c5bae-5b20-4dcb-9989-79c5dd33996d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=9288ACBF88ACA2E9 /data           ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Here's fdisk -lu output after I add /dev/sdc1 to fstab.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a1d92ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   152103419    76051678+   7  HPFS/NTFS
/dev/sda2       152103420   156296384     2096482+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x320a1743

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   152103419    76051678+  83  Linux
/dev/sdb2       152103420   156296384     2096482+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x009cf485

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   156296384    78148161    7  HPFS/NTFS

```

When I reboot my PC, my "DATA" does not show up.  If I remove it from fstab, it's back and I can mount it just fine but it's under "/media/DATA".

Why can I not add it to fstab and have it show up?

---

### Post by taurus on 2008-12-10
Can you also post the output of this command from a terminal?

```
sudo blkid
```

---

### Post by EvilRick on 2008-12-10
```

/dev/sda1: UUID="BA74C82874C7E4EB" LABEL="WINXPPRO" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="2e28f1b0-afc0-4bac-8cfa-6c65e162340e" 
/dev/sdb1: UUID="1f6c5bae-5b20-4dcb-9989-79c5dd33996d" TYPE="ext3" 
/dev/sdb2: UUID="433FBB1136C3422C" LABEL="SWAP" TYPE="ntfs" 
/dev/sdc1: UUID="9288ACBF88ACA2E9" LABEL="DATA" TYPE="ntfs"

```

/dev/sdb2 is my WindowsXP "swap" partition.  I don't choose to mount it since it's only a 2GB partition full up with 'pagefile.sys'.

---

### Post by EvilRick on 2008-12-10
Ah, is it because I didn't setup an actual mount point?  Do I need to create "/data" as a mount point?

- EDIT -

Duh!  Simple mistake.  I forgot to create the "/data" mount point.

Nothing to see here, move along . . .

---

