---
title: "Hitachi 2tb external not working"
date: 2010-05-07
forum: Hardware
---

### Post by bcvery on 2010-05-07
I bought a Hitachi "SimpleTech"/"SimpleDrive" 2Tb external harddrive quite a while ago.  It was working fine on 9.10, and then continued to work after 10.04 (64-bit) was installed.  It has however now stopped working.  It is powered, but the drive requires both USB and DC to start.  Although it does start whirring (technical term there :P) and the light turns on when plugged in, it does not show up in /media.  It is also not showing up on command lsusb, but it is clearly getting power from the usb.

All help would be greatly appreciated, thanks all.
Bcvery

---

### Post by srs5694 on 2010-05-07
Try, in no particular order:


[list]
[*]Plug the drive into another computer to see if it works there
[*]Use a different USB cable (if it's not permanently attached)
[*]Unplug the drive, type "dmesg | tail -20", plug the drive in again, wait a few seconds, and then type "dmesg | tail -20" again. New messages indicate kernel detection of the new drive, and may contain diagnostic details. Try to figure them out yourself or post them here. If you see no new messages then that indicates that the drive is very invisible even at a low level (as in a bad cable or completely dead USB electronics).
[/list]


If it looks like the drive is completely non-responsive, it could be that the USB interface is shot, but the drive is still OK. If so, opening it up, removing it, and then installing the disk directly in a computer or putting it in a new external interface may get it working again. This is an extreme step, though, so take it only when you've exhausted other options.

---

