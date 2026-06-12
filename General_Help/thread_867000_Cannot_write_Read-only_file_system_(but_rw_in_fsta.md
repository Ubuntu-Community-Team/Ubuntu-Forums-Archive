---
title: "Cannot write: Read-only file system (but rw in fstab)"
date: 2008-07-22
forum: General Help
---

### Post by mogie on 2008-07-22
My /etc/fstab:

This is not logical. My Ubuntu 6.10 server went like this some days ago, and now I cannot write to /dev/sda1 on  mounted on/media2 (last line). This problem has come all of a sudden.

Any suggestions? /etc/mtab is all the same if you want to know.
I can though "fix" this by running "mount -a", and sda1 then becomes writeable..(why?)

```
/dev/sdb1 on / type ext3 (rw,errors=remount-ro,usrquota,grpquota)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb3 on /boot type ext3 (rw)
/dev/sdb4 on /home type ext3 (rw,usrquota,grpquota)
/dev/sda1 on /media2 type ext3 (rw)

```

---

### Post by dracayr on 2008-07-22
could you please post your fstab file?

dracayr

---

### Post by mogie on 2008-07-22
Got an bad output from my bootup now..

/var/log/fsck/checkfs:
```
Log of fsck -C -R -A -a
Tue Jul 22 18:34:40 2008

fsck 1.39 (29-May-2006)
/dev/hdc3: clean, 31/24096 files, 15307/96358 blocks
/dev/sda1: recovering journal
/dev/sda1 contains a file system with errors, check forced.
Error reading block 9338882 (Attempt to read block from filesystem resulted in short read) while doing inode scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
/dev/hdc4: clean, 20141/47480832 files, 34703159/47472075 blocks
fsck died with exit status 4

Tue Jul 22 18:36:53 2008
----------------

```

Any suggestions what I should do next`? :confused: I really hope I wont loose mye data on this drive. It's reacently bought, and quite new, so I hope it's not any physical damage to it already..

Hers my /var/log/dmesg which is a bit more detailed on what going on under the fsck:
```
[42949385.700000] Adding 489972k swap on /dev/sdb2.  Priority:-1 extents:1 across:489972k
[42949385.820000] EXT3 FS on sdb1, internal journal
[42949395.810000] eth1: no IPv6 routers present
[42949424.040000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949424.040000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949424.040000] ata1: error=0x40 { UncorrectableError }
[42949426.820000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949426.820000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949426.820000] ata1: error=0x40 { UncorrectableError }
[42949429.440000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949429.440000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949429.440000] ata1: error=0x40 { UncorrectableError }
[42949432.070000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949432.070000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949432.070000] ata1: error=0x40 { UncorrectableError }
[42949435.140000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949435.140000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949435.140000] ata1: error=0x40 { UncorrectableError }
[42949437.920000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949437.920000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949437.920000] ata1: error=0x40 { UncorrectableError }
[42949437.920000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[42949437.920000] sda: Current: sense key: Medium Error
[42949437.920000]     Additional sense: Unrecovered read error - auto reallocate failed
[42949437.920000] Info fld=0x4740053
[42949437.920000] end_request: I/O error, dev sda, sector 74711122
[42949437.920000] Buffer I/O error on device sda1, logical block 37355529
[42949440.830000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949440.830000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949440.830000] ata1: error=0x40 { UncorrectableError }
[42949443.440000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949443.440000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949443.440000] ata1: error=0x40 { UncorrectableError }
[42949446.050000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949446.050000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949446.050000] ata1: error=0x40 { UncorrectableError }
[42949448.670000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949448.670000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949448.670000] ata1: error=0x40 { UncorrectableError }
[42949451.270000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949451.270000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949451.270000] ata1: error=0x40 { UncorrectableError }
[42949453.900000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949453.900000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949453.900000] ata1: error=0x40 { UncorrectableError }
[42949453.900000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[42949453.900000] sda: Current: sense key: Medium Error
[42949453.900000]     Additional sense: Unrecovered read error - auto reallocate failed
[42949453.900000] Info fld=0x4740053
[42949453.900000] end_request: I/O error, dev sda, sector 74711123
[42949453.900000] Buffer I/O error on device sda1, logical block 37355530
[42949456.550000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949456.550000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949456.550000] ata1: error=0x40 { UncorrectableError }
[42949459.330000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949459.330000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949459.330000] ata1: error=0x40 { UncorrectableError }
[42949461.960000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949461.960000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949461.960000] ata1: error=0x40 { UncorrectableError }
[42949464.590000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949464.590000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949464.590000] ata1: error=0x40 { UncorrectableError }
[42949467.500000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949467.500000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949467.500000] ata1: error=0x40 { UncorrectableError }
[42949470.260000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949470.260000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949470.260000] ata1: error=0x40 { UncorrectableError }
[42949470.260000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[42949470.260000] sda: Current: sense key: Medium Error
[42949470.260000]     Additional sense: Unrecovered read error - auto reallocate failed
[42949470.260000] Info fld=0x4740053
[42949470.260000] end_request: I/O error, dev sda, sector 74711122
[42949470.260000] Buffer I/O error on device sda1, logical block 37355529
[42949472.860000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949472.860000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949472.860000] ata1: error=0x40 { UncorrectableError }
[42949475.780000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949475.780000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949475.780000] ata1: error=0x40 { UncorrectableError }
[42949478.550000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949478.550000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949478.550000] ata1: error=0x40 { UncorrectableError }
[42949481.320000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949481.320000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949481.320000] ata1: error=0x40 { UncorrectableError }
[42949483.940000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949483.940000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949483.940000] ata1: error=0x40 { UncorrectableError }
[42949486.550000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949486.550000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949486.550000] ata1: error=0x40 { UncorrectableError }
[42949486.550000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[42949486.550000] sda: Current: sense key: Medium Error
[42949486.550000]     Additional sense: Unrecovered read error - auto reallocate failed
[42949486.550000] Info fld=0x4740053
[42949486.550000] end_request: I/O error, dev sda, sector 74711123
[42949486.550000] Buffer I/O error on device sda1, logical block 37355530
[42949489.160000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949489.160000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949489.160000] ata1: error=0x40 { UncorrectableError }
[42949491.790000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949491.790000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949491.790000] ata1: error=0x40 { UncorrectableError }
[42949494.570000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949494.570000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949494.570000] ata1: error=0x40 { UncorrectableError }
[42949497.500000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949497.500000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949497.500000] ata1: error=0x40 { UncorrectableError }
[42949500.130000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949500.130000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949500.130000] ata1: error=0x40 { UncorrectableError }
[42949502.880000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949502.880000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949502.880000] ata1: error=0x40 { UncorrectableError }
[42949502.880000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[42949502.880000] sda: Current: sense key: Medium Error
[42949502.880000]     Additional sense: Unrecovered read error - auto reallocate failed
[42949502.880000] Info fld=0x4740053
[42949502.880000] end_request: I/O error, dev sda, sector 74711122
[42949502.880000] Buffer I/O error on device sda1, logical block 37355529
[42949505.630000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949505.630000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949505.630000] ata1: error=0x40 { UncorrectableError }
[42949508.550000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949508.550000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949508.550000] ata1: error=0x40 { UncorrectableError }
[42949511.170000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949511.170000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949511.170000] ata1: error=0x40 { UncorrectableError }
[42949513.790000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949513.790000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949513.790000] ata1: error=0x40 { UncorrectableError }
[42949516.560000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949516.560000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949516.560000] ata1: error=0x40 { UncorrectableError }
[42949519.160000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[42949519.160000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42949519.160000] ata1: error=0x40 { UncorrectableError }
[42949519.160000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[42949519.160000] sda: Current: sense key: Medium Error
[42949519.160000]     Additional sense: Unrecovered read error - auto reallocate failed
[42949519.160000] Info fld=0x4740053
[42949519.160000] end_request: I/O error, dev sda, sector 74711123
[42949519.160000] Buffer I/O error on device sda1, logical block 37355530
[42949671.320000] input: AT Translated Set 2 keyboard as /class/input/input1
[42949677.850000] kjournald starting.  Commit interval 5 seconds
[42949677.850000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[42949677.850000] EXT3 FS on sdb3, internal journal
[42949677.850000] EXT3-fs: mounted filesystem with ordered data mode.
[42949677.870000] kjournald starting.  Commit interval 5 seconds
[42949677.870000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[42949677.870000] EXT3 FS on sdb4, internal journal
[42949677.870000] EXT3-fs: mounted filesystem with ordered data mode.
[42949677.920000] kjournald starting.  Commit interval 5 seconds
[42949677.920000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[42949677.920000] EXT3 FS on sda1, internal journal
[42949677.920000] EXT3-fs: mounted filesystem with ordered data mode.

```

---

### Post by vanadium on 2008-07-22
> /dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)

This tells you to run fsck manually, i.e. from the command prompt. Before doing this, unmount the partition.

```

sudo umount /dev/sda1
sudo fsck /dev/sda1

```

---

### Post by mogie on 2008-07-26
Thanks! it did work out :)

Though, I'm not sure of why it occured. I'll need to run som bad sector tests afterwards. Any idea what may happend?

It had to rewrite only one folder or something. It asked me to fix, and I pressed "yes" every time. All JPG files in specific folder, so I dont know.. :p

I'll return some answers if I find out anything morebout this. Thanks so far!

---

### Post by caljohnsmith on 2008-07-26
I would check the integrity of your HDD if I were you just to be safe. If you have a SMART enabled HDD (most modern ones have that feature set), you can have the HDD run its own tests on itself to check its integrity. To see if the HDD uses SMART technology, you can use either of the following:
```
sudo smartctl -a /dev/sda
sudo hdparm -I /dev/sda
```
So if your HDD is SMART enabled, here's how to tell your HDD to scan itself to check for errors:
```
sudo smartctl -t long /dev/sda
```
Note the above command tells the HDD to run its own test, so the command will terminate while the HDD keeps testing itself. Results/progress are found with the smartctl -a command above.

---

### Post by mogie on 2008-07-29
how do I install the smartctl in ubuntu? cant find the package :p

---

### Post by drs305 on 2008-07-29
> **mogie said:**
> how do I install the smartctl in ubuntu? cant find the package :p

This will install it:
```
sudo aptitude install smartmontools
```

---

### Post by mogie on 2008-08-02
I got a disk crash now.. trying to recover som bad sectors with HDD-Regenerator v3.0, but I'd rather like a linux-cmd which can copy data from the disk and ignoring bad sectors.. 

I hope that's possible? :sad:

---

### Post by sefs on 2008-08-02
Sounds like a job for dd_rescue.

Read this.. 

[http://achmadz.blogspot.com/2007/11/backing-up-partition-using-linux-live.html](http://achmadz.blogspot.com/2007/11/backing-up-partition-using-linux-live.html)

... and see if this will work for you.

---

### Post by mogie on 2008-08-02
I though got a problem..

I dont have any 500GB disk which can be copied too.. :( The largest I have is a 320GB disk..

Is it possible to bkp just a part of the HDD? let's say from sector 4000k etc, with dd_rescue? Is there any other program I may could use instead`?:confused:

---

