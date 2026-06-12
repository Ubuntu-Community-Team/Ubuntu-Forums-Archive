---
title: "cdrom-detect problem with TEAC CD-224E"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by donryan on 2009-01-30
On an 8 year old Dell PowerEdge 6450, I can boot from the CD-ROM drive but cdrom-detect fails. As per the advice given in the Installation Guide (under Troubleshooting the Installation Process), I had a look in /var/log/syslog. The most relevant-looking parts are listed below. I'm hoping to get some help decoding it. Specifically:

(i) Does the fact that the make and model is listed at one stage (TEAC CD-224E) mean that the drive is being properly detected and is supported?

(ii) Does the I/O error stuff and the CRC error indicate a bad CD (rather than a problem detecting the drive)? The CD is OK on the machine that I used to write it, but I read somewhere that it can be better to not do a full-speed write. I tried a second at a lower write speed, but it similarly failed. Possibly a proper CD-ROM rather than a burned CD-R might be what I need.

(iii) Other than that, there's no firmware upgrade for the TEAC CD-224E listed on the Dell support site, and none of the other bits of advice in the Installation Guide apply, so I'm kind of stumped.

Thanks in advance,

Don.

---------/var/log/syslog output -----------------
[...snip...]
ata1.00: ATAPI: TEAC CD-ROM CD-224E, 3.7C, max UDMA/33
ata1.00: configured for UDMA/33
scsi 2:0:0:0 CD-ROM        TEAC CD-224E 3.7C, PQ:0 ANSI:5
scsi 2:0:0:0 Attached scsi generic sg0 type 5
[...snip...]
Driver 'sr' needs updating - please use bus_type methods
sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 2:0:0:0 Attached scsi CD-ROM sr0
scsi 4:4:6:0: Processor DELL 1x4 U2W SCSI BP 1.30 PQ:0 ANSI: 2
sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current]
sr 2:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
end_request: I/O error, dev sr0, sector 40
Buffer I/O error on device sr0, logical block 5
Buffer I/O error on device sr0, logical block 6
Buffer I/O error on device sr0, logical block 7
Buffer I/O error on device sr0, logical block 8
Buffer I/O error on device sr0, logical block 9
Buffer I/O error on device sr0, logical block 10
Buffer I/O error on device sr0, logical block 11
[...snip...]
cdrom-detect: CD-ROM mount failed: device=/dev/scd0
[...snip...]
(process: 3955): mount: mounting /dev/scd0 on /cdrom failed: Input/output error

---

### Post by dabl on 2009-01-30
Try burning a CD in DAO mode, 4X burn speed (after you verify the md5 sum on the downloaded ISO). :)

---

### Post by ejprinz on 2009-02-01
I tried to install the 8.10 LiveCD on several PC's, and had similar Buffer I/O errors using a CD (which passed the media check). However, when I wrote the same iso image onto a DVD instead, the same drives worked without having any errors. Also, the same iso image on a USB stick also worked. So, there seems to be something wrong with the 2.6.27 kernel with certain CD drives.

---

