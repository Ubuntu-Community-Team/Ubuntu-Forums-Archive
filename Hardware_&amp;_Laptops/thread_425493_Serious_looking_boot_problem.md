---
title: "Serious looking boot problem"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by colinireland on 2007-04-27
Hey 

I am having a boot-up problem. I am running Ubuntu 6.06 LTS on a Dell Inspirson 6000. 

Basically how this problem came about is my computer froze and I couldn't seem to do anything about it. Being the impatient person that I am I just held down the power button to turn it off and rebooted.  I got a similar output to the one below so I tried rebooting again in safe mode to see if that would do anything

The usual displays came up on the screen untill "Mounting root files"

The screen then started giving me this output:

[17185389.800000] ata1: status=0xd0 { busy }
[17185389.800000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17185389.800000] sda: Current: sense key: Aborted Command
[17185389.800000]        Additional sense: Scsi parity error
[17185389.800000] end_request: I/O error, dev sda, sector 6199
[17185389.604000] JBD: Failed to read block at offset 233
[17185389.604000] JBD: IO error -5 recovering block 233 in log
[17185389.800000] ata1: command 0x25 timeout, stat 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00

[17186688.800000] ata1: status=0xd0 { busy }
[17186688.800000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17186688.800000] sda: Current: sense key: Aborted Command
[17186688.800000]       Additional sence: Scsi parity error
[17186688.800000] end_request: I/O error, dev sda, sector 88080511
[17186688.800000] Buffer I/O error on device sda1, logical block 11010058
[17186688.800000] lost page write due to I/O error on sda1
[17186688.800000] ata1: command 0x35 timeout, stat 0xd0 host_stat 0x21
[17186688.800000] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00

I have left my Laptop running for well over 2hrs now and this message keeps coming up obviously with changes to the sector number.

I would really appreciate some help here as I have no idea what is going on. I have alot of data that I dont want to lose so a reinstallation of the OS is not really an option for me.

Also I am interested in finding out what exactly output means

Thanks,
Colin

---

### Post by abc123456 on 2007-04-27
The errors are about the scsi hard drives.  Check and see if the cable is connecting.  Also doesn't Dell have a jumper to turn on scsi?

Hope this helps.:)

---

### Post by colinireland on 2007-04-27
I am pretty new to this side of computers. I dont understand what you recommended. What cable?

Cheers

---

