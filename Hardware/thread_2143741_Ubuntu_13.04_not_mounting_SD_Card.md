---
title: "Ubuntu 13.04 not mounting SD Card"
date: 2013-05-09
forum: Hardware
---

### Post by gsingh2011 on 2013-05-09
I'm trying to mount a SanDisk 16GB SDHC Card into my laptop running Ubuntu 13.04. The card reader is built in. When I plug in the card I don't see anything. When I run

```
tail -f /var/log/syslog
```

I get
```
May  9 22:41:03 gulshan-hp kernel: [ 1036.744421] mmc1: error -110 whilst initialising SD card
May  9 22:41:04 gulshan-hp kernel: [ 1037.718730] mmc1: new SDHC card at address e624
May  9 22:41:04 gulshan-hp kernel: [ 1037.719151] mmcblk0: mmc1:e624 SD16G 14.8 GiB 
May  9 22:41:04 gulshan-hp kernel: [ 1037.919128] mmcblk0: error -110 sending status command, retrying
May  9 22:41:04 gulshan-hp kernel: [ 1038.018951] mmcblk0: error -110 sending status command, retrying
May  9 22:41:04 gulshan-hp kernel: [ 1038.118915] mmcblk0: error -110 sending status command, aborting
May  9 22:41:04 gulshan-hp kernel: [ 1038.118931] end_request: I/O error, dev mmcblk0, sector 0
May  9 22:41:04 gulshan-hp kernel: [ 1038.118938] quiet_error: 66 callbacks suppressed
May  9 22:41:04 gulshan-hp kernel: [ 1038.118943] Buffer I/O error on device mmcblk0, logical block 0
```

Also
```
ls -l /dev/sd*
```

doesn't show the SD card and neither does lsusb.

Does anyone have any idea what's wrong?

Edit: Also, this SD card is from my Canon T3i and the images show up fine there. So the SD card isn't corrupted.

---

### Post by akira_sp on 2013-06-14
Same problem here with my Sony Vaio laptop and Sony SD card... worked fine on Ubuntu 12.04. Not working since the upgrade :(

---

### Post by scbingham on 2013-06-14
Doesn't really help you chaps but it seems internal card readers are rather a hit or miss affair, even between different OS versions. Cheap external usb card readers seem to just work.

Just my two pennies worth.

---

### Post by nik_nah on 2013-06-14
I had a problem with my SD card recently.  It worked with the camera, but didn't work on the computer or and card readers.

But when I looked at the free space in the camera it was half full when I had removed most of the images.
After reformatting, it was working again.

---

