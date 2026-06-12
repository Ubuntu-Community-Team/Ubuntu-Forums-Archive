---
title: "DVD bruner wont read DVD+R DL"
date: 2009-07-28
forum: Hardware
---

### Post by zodiac09 on 2009-07-28
Hey there. i am trying to burn a DVD+R DL. but ubuntu wont pick up the disc. I was wondering if someone else had this problem and could help me out? I can burn DVD-R and CD-R fine. I know my burner can support DVD+R DL. I have burned them under windows when i first bought this laptop. Here is a link to my computers specs.

 [http://support.gateway.com/s/Mobile/2008/Tempest/1015715R/1015715Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/Tempest/1015715R/1015715Rsp2.shtml)


 I am thinking i need to change the Optiarc driver, Right now ubunut says its using Optiarc DVD RW AD-7560a . and i can't find out if that support DVD+R DL or not. but i don't know. any help or xtra knowledge would be a great help! THanks.

---

### Post by zodiac09 on 2009-07-28
oh yeah. i am running Ubuntu 9.04 Jaunty

---

### Post by zodiac09 on 2009-07-28
i looked in my BIOS and it does say Optiarc DVD RW AD-7560a. So it should be using that. I just don't know.

---

### Post by zodiac09 on 2009-07-29
Here is the output of cdrecord -v checkdrive

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7560A '
Revision       : 'DX06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1326417898 = 1295329 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
wodim: No such file or directory. Cannot open 'checkdrive'.

---

