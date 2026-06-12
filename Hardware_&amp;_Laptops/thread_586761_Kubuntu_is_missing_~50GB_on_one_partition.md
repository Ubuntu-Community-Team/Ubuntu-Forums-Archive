---
title: "Kubuntu is missing ~50GB on one partition"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by AllesMeins on 2007-10-22
Hi,

one of my ext3-partitions should be ~118 GB in size but is reported as only 48GB by df -h and konqueror. parted reports it correctly as being ~118 GB. I've already tried e2fsck and a S.M.A.R.T-Test with no error found.


Output from df -h:

```

Filesystem            Size  Used Avail Use% Mounted on
[...]
/dev/sdb5              12G   12G  501M  96% /media/sdb5
/dev/sdb6              12G  9.9G  1.9G  84% /media/sdb6
/dev/sdb7              16G  8.6G  7.2G  55% /media/sdb7
/dev/sdb8              48G   38G  7.4G  84% /home/gedinixan/backups
[...]

```

Output from parted:

```

Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      8225kB  160GB   160GB   extended               lba
 5      8258kB  12.6GB  12.6GB  logical   ntfs
 6      12.6GB  25.2GB  12.6GB  logical   ntfs
 7      25.2GB  42.0GB  16.8GB  logical   ntfs
 8      42.0GB  160GB   118GB   logical   ext3

```

System is Kubuntu Gutsy on amd64.

Any ideas how i can restore (and use) the full partition-size?

---

### Post by AllesMeins on 2007-10-25
Does nobody have an idea?

---

