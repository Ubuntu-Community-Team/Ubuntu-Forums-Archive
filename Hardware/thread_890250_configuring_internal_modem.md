---
title: "configuring internal modem"
date: 2008-08-14
forum: Hardware
---

### Post by piobair on 2008-08-14
Once upon a time (prior to Ubuntu 8 ), the internal modem on my Thinkpad X41 worked. That was then.

wvdialconf only reports modems connected to serial ports tty0 - tty3. I understand that setserial is required for USB connected stuff. 
more |proc |bus|usb |devices
  ...
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: IBM Unknown device 0574
        Flags: medium devsel, IRQ 18
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: [50] Power Management version 2

Do I need to MAKEDEV? 
What port do I tell KPPP to connect to?
The WIKI page is looking for a /dev/ttyUSB* . I do not have such. What I do have is 
# ls /dev/usbdev*
/dev/usbdev1.1_ep00  /dev/usbdev3.1_ep81  /dev/usbdev4.1_ep00
/dev/usbdev1.1_ep81  /dev/usbdev3.2_ep00  /dev/usbdev4.1_ep81
/dev/usbdev2.1_ep00  /dev/usbdev3.2_ep02  /dev/usbdev5.1_ep00
/dev/usbdev2.1_ep81  /dev/usbdev3.2_ep81  /dev/usbdev5.1_ep81
/dev/usbdev3.1_ep00  /dev/usbdev3.2_ep83

Advice?

---

