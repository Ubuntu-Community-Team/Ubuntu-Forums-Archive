---
title: "force dual monitor on Dell Latitude D505"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by RevNomad on 2005-10-17
Before WinXP died on this machine I was able to use the LCD screen and the projector.  Ubuntu forces one or the other.  I need both if at all possible.  Is there a fix, either software or (cheap) hardware, such as a USB to VGA cable?

Thanks in advance
Norman

---

### Post by simohell on 2005-10-17
It might be enough to add the following lines to your xorg.conf file.
The file xorg.conf should be found at /etc/X11/xorg.conf

```

Option "MonitorLayout" "LFP, CRT"
Option "Clone" "On"

```

So your video card section would probably look something like this:

```

Section "Device"
    Identifier  [Your video card name]
    BusID      [Your videocard's BusID]
    Driver      "i810"
    Option     "MonitorLayout" "LFP, CRT"
    Option      "Clone" "On"
EndSection

```

For more options available for your video card you can type: man i810

---

### Post by RevNomad on 2005-12-07
OK, after upgrading to Breezy I tried editing the xorg.conf file.  GDM wouldn't even load until I took out the edits.

Looking for more advice.

Thanks for helping.

NTP

Update:  Don't ask because I don't understand but it works.  Yea!!!!!!!!!!!!!!!!!!!!!!!!1

---

