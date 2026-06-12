---
title: "mt-st reports incorrect tape drive type"
date: 2010-07-05
forum: Hardware
---

### Post by ka1ssr on 2010-07-05
I am having trouble getting mt (mt-st) to report the correct SCSI tape drive.  I followed the instructions on thread [http://ubuntuforums.org/showthread.php?t=56902]("http://ubuntuforums.org/showthread.php?t=56902") and when I inserted a tape and executed mt -f /dev/st0 status it showed that I had a DDS-2 drive, which is correct.  However, when I executed an erase command the status command reported that I had an EX-8505 compressed drive attached.  I should note that "dpkg-reconfigure mt-st" executed with no messages, so I don't know if it worked or not.

While it is possible to read and write tapes I would feel a bit better if mt knew what kind of drive it was talking to.

Or is an Exabyte EXB-8505 similar to a DDS-2 drive?

Oh yeah, cat /proc/scsi/scsi says:

```
ka1ssr@ernie:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 2F040L0   Rev: VAM5
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: WDC WD153BA      Rev: 16.1
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: SAMSUNG  Model: CDRW/DVD SM-308B Rev: T100
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ARCHIVE  Model: Python 02635-XXX Rev: 5.AO
  Type:   Sequential-Access                ANSI  SCSI revision: 02
```

And /etc/stinit.def is...

```
ka1ssr@ernie:~$ cat /etc/stinit.def
# This file contains example definitions for different kinds of tape
# devices. 
#
# You can find some examples in /usr/share/doc/mt-st/examples.
#
# Common definitions to be applied to all tape devices
# (This is the driver's default)
{buffer-writes read-ahead async-writes}

# A compressing DAT (DDS-1-DC or DDS-[234])
manufacturer=ARCHIVE model = "Python 02635-XXX" {
can-bsr can-partitions auto-lock
mode1 blocksize=0 compression=1
mode2 blocksize=1024 compression=1
mode3 blocksize=0 compression=0
mode4 blocksize = 1024 compression=0 }
```

Thanks for your help!

---

