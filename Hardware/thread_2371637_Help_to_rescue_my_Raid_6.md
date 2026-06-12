---
title: "Help to rescue my Raid 6"
date: 2017-09-16
forum: Hardware
---

### Post by huangyingw on 2017-09-16
I had a raid 6 by mdadm, with 4 x 3TB hard disks.
I don't have partitions on the drives, just used "bare metal" to create the raid. The raid 6 works well in my old PC, until recently I move them to my new PC(with UEFI support). I could not assemble them at all, and I move them back to my old PC, and with a new Ubuntu OS 16.04, I could neither assemble at all. 

On my old pc, they would be recognized like, take /dev/sdb as example:
```
/dev/sdb: UUID="599ce008-859c-f8b6-ee29-e7e6c75e77c5" UUID_SUB="00177490-172b-32f9-773a-b87f4d87ee4c" LABEL="nas:1" TYPE="linux_raid_member"

```
But now, in my new PC with ubuntu 16.04, they are recognized like:
```
/dev/sdb: PTUUID="7e4bb82c-1d07-4294-a4ab-25acb84b996a" PTTYPE="gpt"
```

Now the output of gdisk is
```
gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7E4BB82C-1D07-4294-A4AB-25ACB84B996A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
```

---

### Post by TheFu on 2017-09-16
$ sudo mdadm --details .... if that does anything useful. Might not.
and the content from the /etc/mdadm/mdadm.conf from the last working system could be helpful.

I would wipe the disks, create a new mdadm array and restore into it from my backups.
RAID5/6 aren't recommended for HDDs over 2TB in size, btw.

---

