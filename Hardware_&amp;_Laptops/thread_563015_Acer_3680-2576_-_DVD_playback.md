---
title: "Acer 3680-2576 - DVD playback"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by malignor on 2007-09-29
Aloha.

Whenever I try to play a DVD, or a .vob file from a DVD, the player greys out and crashes.

Video players I've tried:
[LIST][*]Kaffiene[*]xgine[*]totem movie player[*]ogle[/LIST]

Installed the w32 and other DVD codecs ("sudo apt-get install libdvdcss2 w32codecs")

Heres the setup dmesg for rc0 (the DVD ROM)...
[    4.676000] sd 0:0:0:0: Attached scsi disk sda
[    4.676000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.676000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.680000] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.680000] Uniform CD-ROM driver Revision: 3.20
[    4.680000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.868000] Attempting manual resume
[    4.868000] swsusp: Resume From Partition 8:5
[    4.868000] PM: Checking swsusp image.
[    4.868000] PM: Resume from disk failed.

and the results when I try to play a DVD...
[ 1412.948000] sr0: Current: sense key: Medium Error
[ 1412.948000] end_request: I/O error, dev sr0, sector 11202228
[ 1412.948000] Buffer I/O error on device sr0, logical block 2800557
[ 1412.948000] Buffer I/O error on device sr0, logical block 2800558
[ 1412.948000] Buffer I/O error on device sr0, logical block 2800559
[ 1418.896000] sr0: Current: sense key: Medium Error
[ 1418.896000] end_request: I/O error, dev sr0, sector 11202228
[ 1418.896000] Buffer I/O error on device sr0, logical block 2800557
[ 1424.840000] sr0: Current: sense key: Medium Error
[ 1424.840000] end_request: I/O error, dev sr0, sector 11202232
[ 1424.840000] Buffer I/O error on device sr0, logical block 2800558
[ 1424.840000] Buffer I/O error on device sr0, logical block 2800559
[ 1430.716000] sr0: Current: sense key: Medium Error
[ 1430.716000] end_request: I/O error, dev sr0, sector 11202232
[ 1430.716000] Buffer I/O error on device sr0, logical block 2800558
[ 1430.716000] Buffer I/O error on device sr0, logical block 2800559

... or just a video file from a DVD...
[ 1262.544000] end_request: I/O error, dev sr0, sector 14364944
[ 1262.588000] end_request: I/O error, dev sr0, sector 14364944
[ 1263.048000] end_request: I/O error, dev sr0, sector 14364944
[ 1263.096000] end_request: I/O error, dev sr0, sector 14364944
[ 1263.144000] end_request: I/O error, dev sr0, sector 14364944

Is there something I haven't tried?
I know the drive works for music playback, as I've used it. Data is a non-issue.
I be stumped. :P
Ideas?

---

### Post by linuxwizard on 2007-09-29
These also needs to be installed for DVD   libdvdread3 and libxine1-ffmpeg . Are they installed ? Can be installed through Synaptic.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by malignor on 2007-09-30
Unfortunately, I have.

Indeed, I'm running Feisty Fawn.

libdvdread3
libxine1-ffmpeg
libdvdcss2

All these are installed and updated.

The SCSI I/O errors suggest something involving direct access... possibly DMA, but I know I have it applied. Are there more than one DMA modes I can set?

---

### Post by linuxwizard on 2007-09-30
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by laborg on 2007-10-14
Hi!

I suffer under the same problem with gutsy gibbon since a couple of days. did you find a solution?

greetings gerhard

---

