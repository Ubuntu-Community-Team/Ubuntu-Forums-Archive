---
title: "USB devices no longer working."
date: 2008-06-06
forum: Hardware
---

### Post by murphykieran on 2008-06-06
I've been using Ubuntu for a while now and everything has been running pretty smoothly until a while back when all my USB devices stopped working.  Before, my printer/scanner/digital camera/external HDD/memory sticks etc. were all working fine, but all of a sudden they've all stopped working and the system doesn't recognise any of them.

I've checked the computer BIOS and the USB ports are enable ok.

I did a bit of a search and it was suggested to type in the following command to see what it said as it might be helpful in troubleshooting.  Well here it is and the output.  When I plug in a USB device, nothing happens.   The lines with -- MARK -- at the end were after I entered the command and before I plugged in the USB memory stick.
```
kieran@kieran-desktop:~$ tail -f /var/log/messages
Jun  6 10:42:17 kieran-desktop -- MARK --
Jun  6 11:02:17 kieran-desktop -- MARK --
Jun  6 11:22:17 kieran-desktop -- MARK --
Jun  6 11:42:17 kieran-desktop -- MARK --
Jun  6 12:02:17 kieran-desktop -- MARK --
Jun  6 12:22:17 kieran-desktop -- MARK --
Jun  6 12:42:17 kieran-desktop -- MARK --
Jun  6 13:02:17 kieran-desktop -- MARK --
Jun  6 13:22:17 kieran-desktop -- MARK --
Jun  6 13:42:17 kieran-desktop -- MARK --

```It doesn't matter if I connect my digital camera or another USB stick or use the front or rear USB ports, nothing is happening.

Is there anyway to tell if it's just a problem within Ubuntu or if there's a hardware problem?

---

### Post by Sef on 2008-06-06
Do you have a Live CD handy?  If so, use that and see if you can use your usb ports or not.

---

### Post by murphykieran on 2008-06-06
> **Sef said:**
> Do you have a Live CD handy?  If so, use that and see if you can use your usb ports or not.Oh, never thought of that. I still have the Ubuntu Live CD here, so I'll boot to it and see if the USB is working.

Thanks for the suggestion.

---

### Post by murphykieran on 2008-06-06
Nuts, the USB still isn't working when I boot to the Ubuntu CD.  I tried a couple of devices on both the front and rear ports and no luck and they're working okay on a Windows XP PC I have here.

Oh well, looks like it's not a software issue and I need a new mainboard... :(

---

