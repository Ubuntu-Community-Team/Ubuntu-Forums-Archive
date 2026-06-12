---
title: "[SOLVED] Automounting not working?"
date: 2008-12-03
forum: Hardware
---

### Post by andreasis on 2008-12-03
I have a a Samsung YP-F2J mp3 player, and it required no special drivers on a windows machine, as it was recognized as a mass storage device.  I'm running intrepid with all the latest updates, and my usb stick and external hdd are mounted automatically by ubuntu when I plug them in.  The mp3 player fails to mount, however.  It does not show up in /media/

```
s@x:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 043d:010b Lexmark International, Inc. 2500 Series
Bus 003 Device 002: ID 046d:c50c Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 067b:2506 Prolific Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Who's got some ideas?

---

### Post by NullHead on 2008-12-03
It could be an MTP device. Make sure libmtp is installed, and try accessing it from Rhythmbox.

---

### Post by andreasis on 2008-12-04
Thank you for that tip.  You are right, and libmtp8, libmtp-doc and libmtp-dev are now installed.

I went into rhythmbox, edit>plugins and I enabled 'Portable Players - MTP'

Now there is a different issue:

```
s@x:~$ rhythmbox

(rhythmbox:16296): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate

(rhythmbox:16296): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
PTP: Opening session
Segmentation fault
```

```
s@x:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Samsung: YP-F2J (04e8:5057) @ bus 0, dev 18
Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
Segmentation fault

```

```
s@x:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 043d:010b Lexmark International, Inc. 2500 Series
Bus 003 Device 002: ID 046d:c50c Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 067b:2506 Prolific Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 018: ID 04e8:5057 Samsung Electronics Co., Ltd 
Bus 004 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by NullHead on 2008-12-04
Unplug and replugin the device like was said in the first code snippet you posted. If that doesn't work, I suggest installing banshee, bmpx or songbird and try out those players. They also have support for mtp devices.

---

### Post by andreasis on 2008-12-04
NullHead, I am going to stick with rhythmbox now that it finally works.  Out of curiosity, do you know if rhythmbox's mtp plugin depends on libmtp?

I went ahead and upgraded to libmtp 0.3.4 from sourceforge.  While mtp-detect and mtp-files still segfault on me, rhythmbox doesn't give me any problems anymore and the device is recognized.

Thank you for being the only person to help me with this.

---

