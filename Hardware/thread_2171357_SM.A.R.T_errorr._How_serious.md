---
title: "S:M.A.R.T errorr. How serious?"
date: 2013-08-30
forum: Hardware
---

### Post by Azyx on 2013-08-30
I have a disk that have only run for 177 days as an USB-disk. I have empty the disk and get rid of partition and also the MBR and run a Benchmark with read and write.  I run a SMART self-test and get a warning about a few bad sectrors (1457 sectrosr) se screenshot below.

I wonder if the error may have occoured with a glitching USB-connection, or if there are a real problem with the HDD?

Is there a way to stress-test the HDD?

I have now put the HDD in a machin true the SATA interface.

Cheers, and are grateful with al tips and experience of failing HDD :) /Azyx

---

### Post by ibjsb4 on 2013-08-30
Its a warning, not a failure.  I got the same warning on a old HDD about a half a year ago and its still in service.  To me it means it could last a long time or it could fail tomorrow.

---

### Post by Yellow Pasque on 2013-08-30
I would try using badblocks to test some of the sectors: [http://unix.stackexchange.com/questions/25902/what-does-this-hard-disk-error-message-mean-current-pending-sector-count](http://unix.stackexchange.com/questions/25902/what-does-this-hard-disk-error-message-mean-current-pending-sector-count)
If they come out good, then a USB-specific issue is the likely culprit.


Note: you can use 'fdisk -l ' command to get the block size

---

### Post by prodigy_ on 2013-08-30
1500 bad sectors is a lot and SMART is telling you it's only gonna get worse (not surprisingly). But how serious it is for *you* only you can decide. For some people 1 bad sector = trash can time. Others keep using failing disks till the last possible moment.

In any case make a backup and move any important data off that disk.

---

### Post by CharlesA on 2013-08-30
SMART readings aren't standardized, so it may be the drive throwing erroneous messages, but it would be a good idea to backup your data if you haven't done so already, just in case.

Anyway +1 to badblocks.

---

### Post by prodigy_ on 2013-08-30
> **CharlesA said:**
> Anyway +1 to badblocks.
Bad blocks always win. ;)

---

### Post by Azyx on 2013-08-30
I don't have any data on theb disk. I wonder if i should troe the disk away

---

### Post by CharlesA on 2013-08-30
Just run badblocks on it. If the power on hours are only 177 days, the disk isn't even six months old (if it was powered on 24/7 at least).

---

### Post by Azyx on 2013-08-30
Thanx. I will run badblock when I'm sober :)'

---

### Post by Azyx on 2013-09-01
I run:
```
Azyx@Blackus:~$ sudo fdisk -l /dev/sdc
[sudo] password for Azyx: 

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
Azyx@Blackus:~$ sudo badblocks -b 512 /dev/sdc
```

It has run for hours now, with just a blinking cursor. Do I need to make a partition table before?

---

### Post by CharlesA on 2013-09-01
No, you are fine. Unless you use -s when starting badblocks, it won't show anything.
[http://linux.die.net/man/8/badblocks](http://linux.die.net/man/8/badblocks)

---

### Post by Azyx on 2013-09-01
I have run 'sudo badblocks -s -b 512 /dev/sdc' but after the test nothing reported as bad sectors. Have I missed something, or does the disk don't have any bad sectrors?

---

### Post by CharlesA on 2013-09-01
You should be fine. The drive is either throw incorrect SMART data (likely) or the program isn't reading it correctly.

If you really want to check it, use the tools from the disk manufacturer to check the drive.

---

### Post by Azyx on 2013-09-02
Thanx. I find a dos-application on WD homepage. That should work under wine, or?

[URL="http://support.wdc.com/product/download.asp?groupid=608&sid=2&lang=en"]http://support.wdc.com/product/download.asp?groupid=608&sid=2&lang=en
[/URL]

Need to create a 'DOS-boot diskett' but there was also a windows app, that start under Wine:

[http://support.wdc.com/product/download.asp?groupid=608&sid=3&lang=en]("http://support.wdc.com/product/download.asp?groupid=608&sid=3&lang=en")

I find now that there are a Windows app, but it only shows FAT32 and NTFS-partitions. Maybe I need to create a partition in FAT32 or a NTFS before I run the test application?

I really hate windos..or more precisly, administrate it...

---

### Post by CharlesA on 2013-09-02
[FreeDOS]("http://www.freedos.org/") should let you boot the DOS diagnostics, or you could just download a [boot disk]("http://bootdisk.com/bootdisk.htm"), but most of the ones I found were packaged in EXEs.

Good luck.

---

### Post by Azyx on 2013-09-03
Thanx. Will try it, later. I don't have any CDoch Floppy...And by the way, does,t I need a lot of drivers to the machine?  I have completly forget that stufff ;)

---

### Post by CharlesA on 2013-09-03
I have no idea, as I do not use FreeDOS.

---

### Post by Azyx on 2013-09-07
Now since the last week, the number of 'few bad sectors', has decline from 1457 to 1137 :)  I see that as a sign that S.M.A.R.T only report then they classified a sector as bad and just update then the file system write to the asumed bad sector?

I think I can use the hdd...

---

### Post by CharlesA on 2013-09-07
Just be sure you are doing backups. :)

---

### Post by Azyx on 2013-09-07
can't make backups for 1TB

---

### Post by CharlesA on 2013-09-07
No backup drive then?

---

