---
title: "USB scanner doesn't work"
date: 2013-12-16
forum: Hardware
---

### Post by elson2 on 2013-12-16
I just updated to Ubuntu 12.04 X86_64, and can't get my scanner to work.
It is a Mustek Bear Paw 1200 CU, which uses the sane gt68xx backend,
with the ps1fw.usb firmware (vendor/device id is 05d8:4002)
I installed the firmware, but the scanner doesn't seem to work.

sane-find-scanner reports :
found USB scanner (vendor=0x05d8, product=0x4002, chip=GT-6801) at libusb:002:003

scanimage -L reports :
device `gt68xx:libusb:002:003' is a Mustek BearPaw 1200 CU flatbed scanner

But, sane doesn't work, and scanimage > x.pnm gives :
scanimage: sane_start: Device busy

I'm not sure how to debug this.

Thanks for any ideas anyone has.

Jon

---

### Post by dovah on 2013-12-16
Have you tried to install the package **scangearmp**? ```
sudo-apt get install scangearmp
``` It fixed the same issue for me (and we're running the same distro!)

Have a nice day!

ps: then, for scanning, simply run ($sudo) ```
scamgearmp
```

---

### Post by oldos2er on 2013-12-17
Moved to Hardware.

---

### Post by elson2 on 2013-12-17
> **dovah said:**
> Have you tried to install the package **scangearmp**? ```
sudo-apt get install scangearmp
``` It fixed the same issue for me (and we're running the same distro!)

Have a nice day!

ps: then, for scanning, simply run ($sudo) ```
scamgearmp
```

Scangearmp seems to be for Canon multi-function units, has nothing to do with
Mustek scanners.  Well, I got it to work.  First, I was using the wrong firmware
file, there are several called out for scanners that give the same 5d8:4002
ID.  sbfw.usb was the right one.  Then, in the gt68xx.conf file, I had to
give the full path to the firmware file in the firmware command.  Then, it 
started working OK.

Jon

---

