---
title: "dd - hard drive recovery"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by andy90 on 2007-04-20
Hey
I have a 250gig external drive that seems to have got confused.  In windows it is detected but I am told that there is no partition, do i want to format it now?

No, i want the 230 gig of data on there is poss lol

I have tried a dozen apps (paragon, Linux RIP, partition recover this and that etc) and only one found the data structure (all folders and names etc) but it was a demo and not able to get it back.

So talking to some guys at work they recommend looking into using dd to have a go.

Now its fine for backing up the MBR, but what about repairing or modifying ?

Could anyone point me in a direction or give me tips ?

One thing i thought of was to backup up the MBR, and then copy one accross from the other external drive I have (also a 250gig seagate external, same model) and hoping that would work ? niether boot they are just for data storage.

Any advice or pointers are appreciated :)

---

edit - after trying to mount it in linux its erroring, here is the bottom relevant section of dmesg

[I][B][17222721.996000] NTFS-fs warning (device sdb): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17222721.996000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17222721.996000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17222721.996000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/B][/I]


---

Also the MBR for the drive is:

0000-01B0    ____________________________________ 80 01   .........D......
0000-01C0   01 00 07 FE BF C0 3F 00 - 00 00 42 45 1C 1D 00 00   ......?...BE....
0000-01D0   00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00   ................
0000-01E0   00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00   ................
0000-01F0   00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 55 AA   ..............U.

So afaik this has one partition ('the' partition defined) no ?

---

Well the data is all there, I have managed to source an app to retrieve data but im still curios as to what was wrong with it.  

If I use fdisk in ubuntu it tells me that there is no dos/sun/ibm/solaris (etc) partition table found, and that it will create one in memory until i save changes etc.

I still don't get why the partition was bad, it lines up with another MBR ive studied for another drive

---

