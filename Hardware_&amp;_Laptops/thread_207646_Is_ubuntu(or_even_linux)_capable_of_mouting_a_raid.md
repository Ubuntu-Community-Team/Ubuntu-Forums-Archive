---
title: "Is ubuntu(or even linux) capable of mouting a raid0 system at this point?"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by nessus on 2006-07-02
to make it even more complicated: it is a ntfs file system in a SATA raid0 system which i am trying to mount in my current ubuntu distro.

i have search here and google, so far ppl with the same question havent figured out a way yet. but i just dont want to give up and try to ask the question here again.

my basic HD setup is this:
i originally have winxp installed on my sata raid0 system (2X160GB), then i added another IDE and installed ubuntu.
in my /dev, i see sda, sda1 and sda1. i assume they indicate the raid0 system i have in my pc.
i have followed the ubuntu quick starter guide and used following command to excute:
```
sudo mount /dev/sda /media/windows/ -t ntfs -o nls=utf8,umask=0222
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

i tried sda, sda1 and sda2 above with no luck. here is the error returned:
> mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

then i followed what it suggested:
```
dmesg | tail
```
here is the return:
> [17181831.784000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17181831.784000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[17182130.532000] NTFS-fs error (device sda1): ntfs_attr_find(): Inode is corrupt.  Run chkdsk.
[17182130.532000] NTFS-fs error (device sda1): ntfs_read_inode_mount(): Failed to lookup attribute list attribute. You should run chkdsk.
[17182130.532000] NTFS-fs error (device sda1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[17182130.532000] NTFS-fs error (device sda1): ntfs_fill_super(): Failed to load essential metadata.
[17183516.308000] NTFS-fs warning (device sda): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17183516.308000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17183516.308000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17183516.308000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.

anybody with any ideas? or should i simply just give up?:cry:

---

### Post by el3ktro on 2006-07-02
No, /dev/sda is ONE harddisk. If you have two harddisks in your system, they're sda and sdb. RAID devcies are called md?, so first you have to enable this RAID device, with your commands you're trying to access one of the two RAID harddisks, which of course doesn't work.

Tom

---

### Post by nessus on 2006-07-02
hi, el3ktro

can u be more specific? as i am new to linux world.

i see 25 of md? in my dev, md0~md24.

so how do i mount this ntfs sata raid0 in my system?

---

