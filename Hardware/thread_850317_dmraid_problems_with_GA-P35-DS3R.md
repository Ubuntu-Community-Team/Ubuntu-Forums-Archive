---
title: "dmraid problems with GA-P35-DS3R"
date: 2008-07-05
forum: Hardware
---

### Post by oyvindne on 2008-07-05
I have installed ubuntu (7.10 i think) on this machine before, and didnt have any problems using dmraid then. Suddenly the installed ubuntu stopped working, and when I tired to reinstall, then dmraid reported "No RAID disks".

A copy of vista is running just fine on the raid.

I have followed the instructions on [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) and i will post the results of the tests suggested there.

hope somebody are able to help me out, I use the onboard fakeraid (ICH9R) on GA-P35-DS3R. 

results:


[FONT="Courier New"]ubuntu@ubuntu:~$ sudo dmraid -ay
No RAID disks
ubuntu@ubuntu:~$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
No RAID disks
WARN: unlocking /var/lock/dmraid/.lock
ubuntu@ubuntu:~$ sudo dmraid -b
/dev/sdb:    312581808 total, "S0V3J9CP611265"
/dev/sda:    312581808 total, "S0V3J9CP611175"
ubuntu@ubuntu:~$ sudo dmraid -rD
No RAID disks
ubuntu@ubuntu:~$ sudo fdisk -u -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b7c8d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   122882047    61440000    7  HPFS/NTFS
/dev/sda2       122882048   625145855   251131904    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=outputfile skip=312579808
2000+0 records in
2000+0 records out
1024000 bytes (1,0 MB) copied, 0,00647843 s, 158 MB/s
ubuntu@ubuntu:~$[/FONT]

---

### Post by oyvindne on 2008-07-05
I have also found some strange things when i run dmesg. Maybe this has something to do with my problems?


  198.824807] sda: rw=0, want=625145736, limit=312581808
[  198.824810] printk: 12 messages suppressed.
[  198.824813] Buffer I/O error on device sda2, logical block 62782960
[  198.824817] attempt to access beyond end of device
[  198.824819] sda: rw=0, want=625145736, limit=312581808
[  198.824822] Buffer I/O error on device sda2, logical block 62782960
[  198.824832] attempt to access beyond end of device
[  198.824834] sda: rw=0, want=625145848, limit=312581808
[  198.824836] Buffer I/O error on device sda2, logical block 62782974
[  198.824840] attempt to access beyond end of device
[  198.824842] sda: rw=0, want=625145848, limit=312581808
[  198.824845] Buffer I/O error on device sda2, logical block 62782974
[  198.824876] attempt to access beyond end of device
[  198.824879] sda: rw=0, want=625145856, limit=312581808
[  198.824882] Buffer I/O error on device sda2, logical block 62782975
[  198.824885] attempt to access beyond end of device
[  198.824887] sda: rw=0, want=625145856, limit=312581808
[  198.824894] attempt to access beyond end of device
[  198.824896] sda: rw=0, want=625145856, limit=312581808
[  198.824902] attempt to access beyond end of device
[  198.824905] sda: rw=0, want=625145856, limit=312581808
[  198.824910] attempt to access beyond end of device
[  198.824912] sda: rw=0, want=625145856, limit=312581808
[  198.824918] attempt to access beyond end of device
[  198.824921] sda: rw=0, want=625145856, limit=312581808
[  198.824926] attempt to access beyond end of device
[  198.824928] sda: rw=0, want=625145856, limit=312581808
[  198.824935] attempt to access beyond end of device
[  198.824937] sda: rw=0, want=625145800, limit=312581808
[  198.824943] attempt to access beyond end of device
[  198.824945] sda: rw=0, want=625145848, limit=312581808
[  198.824951] attempt to access beyond end of device
[  198.824953] sda: rw=0, want=625145856, limit=312581808
[  198.824959] attempt to access beyond end of device
[  198.824961] sda: rw=0, want=625145856, limit=312581808
[RIGHT][/RIGHT]

---

### Post by prshah on 2008-07-05
> **oyvindne said:**
> I have installed ubuntu (7.10 i think) on this machine before, and didnt have any problems using dmraid then. Suddenly the installed ubuntu stopped working, and when I tired to reinstall, then dmraid reported "No RAID disks".


Have you made any BIOS changes? Eg, failed battery, BIOS update, etc? Some SATA options allow you to use RAID mode or IDE or legacy modes. Maybe you need to toggle any such settings? I cannot be more specific since the options seem to vary from board-to-board and from bios to bios.

Note that you should look at the BIOS _only_ if you have made any recent changes to it, otherwise I think your problem lies elsewhere, and you should not fiddle with any of the BIOS settings.

---

