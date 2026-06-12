---
title: "Mounting NTFS RAID 0 partition on live cd"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by m1tch37 on 2007-01-02
Gday,

My windows pc has locked up. No windows software/boot disks has been able to help me. This has happened before and i have booted from live cd, mounted the partition and copied the files to a USB hardrive. Except this time, i have a RAID 0 setup. I have no idea where to start...

I have a nVIDIA NFORCE4 SLI chipset and am using the onboard RAID controller, that info might be required for drivers etc..

Regards,
Mitch W

---

### Post by steigleitung on 2007-07-26
I've got the exact same question, I'm also using a RAID 0. My problem is that I can't boot Windows anymore, since it gives me the BSOD. So I thought of using the Ubuntu Live CD as a means to try to backup my Windows harddrive. However, when I try to mount the Windows disk, I get this message:

```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/backup
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

fdisk gives this information:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

Does that mean the harddisk(s) are damaged beyond recovery?

---

### Post by ianare on 2007-07-27
The problem with the nvidia 'RAID' setup is that it's not a real RAID set, it's software RAID, therefore you need to load the correct drivers to access your drives. Otherwise you see each disk separately  (as shown above).

It looks like dmraid is what you need.

[http://packages.ubuntu.com/dapper/admin/dmraid](http://packages.ubuntu.com/dapper/admin/dmraid)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

