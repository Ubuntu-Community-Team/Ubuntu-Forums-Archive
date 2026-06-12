---
title: "USB SD Card Reader Disconnects During File Move"
date: 2018-06-29
forum: Hardware
---

### Post by Lambertus on 2018-06-29
**Background**
Ubuntu 18.04, AMD FX8320 chip, Asus MSA99x EVO R2.0 motherboard with USB 2 and 3 ports
Video camera files on SD HC 80 MB/s 32Gb card
Two USB2 SD Card readers
Put SD card in reader and insert into either a USB2 or USB3 port to cut files and paste to internal HDD

**Issues**
If I cut / paste a single large file or a batch of files (max size per file is 4.1Gb) from the SD Card in the reader, then the routine will be interrupted after some amount of file move and the USB drive disconnects from the computer (/media/me/xxx). Move rate starts as 21 MB/s. The port will no longer recognize that card reader or card until a reboot or 10s of minutes have passed.
Makes no difference which USB port is used.
If the SD card is left in the camera and camera is plugged into a USB port then any size batch of files can be copied and the camera will stay connected until all files are moved. Move rate is 3.5 MB/s.
Had same issue with Ubuntu 16.04, 17.04, 17.10 on same hardware

**Questions**
Are the issues caused by the transfer rate? and if so then is the issue the card reader, motherboard port, HDD or OS?
Any way to use the card reader so it completes the moves at the higher transfer rates?

---

