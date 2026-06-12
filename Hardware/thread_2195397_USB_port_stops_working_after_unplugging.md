---
title: "USB port stops working after unplugging"
date: 2013-12-23
forum: Hardware
---

### Post by tarepanda789 on 2013-12-23
[COLOR=#000000][FONT=verdana]I'm on a fresh install of Ubuntu 12.04 and having difficulty with the USB ports. If I have a device plugged into the machine (mouse, keyboard, usb drive, anything) while booting it up, it is recognized. But if I unplug it and plug it back in or plug something new in, it is not recognized. Another thing that happens, is that if there is some sort of power light on the usb device, it briefly goes on when plugged in and then goes off.

Thanks.[/FONT][/COLOR]

---

### Post by sammiev on 2013-12-23
Are you unmount the device first or just pull the USB device out? If you are just pulling it out, try to unmount and then remove. No issues here.

---

### Post by tarepanda789 on 2013-12-23
I've done both and they have no effect - if I plug anything into a USB port after the computer has booted up, it is not detected. I can only get Ubuntu to detect the device if it is plugged in prior to booting, as in plugged in when the computer is off. 

So for example, if I have a USB drive plugged into the computer when it's off then turn the computer on, when Ubuntu boots, the drive will be detected and fully accessible. If I pull the device out, whether I unmount it or not, then plug it back in, it will not be detected.

And just to clarify, if I plug anything into any USB port after booting, it is not detected. I've tried drives, mouse, keyboard. They only work if plugged in before booting up.

---

### Post by sammiev on 2013-12-23
Post the specs and details from your computer so others can jump in and help sort this out. As it is now, we will only be guessing.

---

### Post by tarepanda789 on 2013-12-23
Posting what I think is relevant info ... Let me know if you'd like to know something else.

Machine is an IBM Thinkcentre M52
[http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-60416](http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-60416)

Processor    2x Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory    1796MB (464MB used)
Operating System    Ubuntu 12.04.3 LTS
USB controller    Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
USB controller    Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
USB controller    Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
USB controller    Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
USB controller    Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])

---

