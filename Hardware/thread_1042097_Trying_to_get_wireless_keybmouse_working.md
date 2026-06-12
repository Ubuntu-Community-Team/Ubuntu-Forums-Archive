---
title: "Trying to get wireless keyb/mouse working"
date: 2009-01-17
forum: Hardware
---

### Post by SirRichieRich on 2009-01-17
I have a Keysonic ack-540rf but its not being "activated".

On boot up it says:

> cloop: Initializing cloop v2.02
usb.c: unable to get device descriptor (error=-110)
usb.c: unable to get device descriptor (error=-110)
INIT: Entering runlevel: 5
usb.c: unable to get device descriptor (error=-110)
usb.c: USB device 22 (vend/prod 0x45e/0x284) is not claimed by any driver.
Starting X...

I saw this thread [http://ubuntuforums.org/archive/index.php/t-356280.html]("http://ubuntuforums.org/archive/index.php/t-356280.html")

I tried adding that info to the /etc/X11/xorg.conf to no avail.

The keyb/mouse is driverless and uses hid. It works on xp, 360 and ps3.

Im actually using a Damn Small Linux build on the xbox, but I believe the key lies with editing the xorg.conf, like that thread mentioned. I cant seem to add a reply on it so I made this new thread. The xbox uses usb1 so should be ok and the wireless keyb/mouse doesnt use usb2. It works with normal usb keyboards or mice.

Any help much appreciated.

---

