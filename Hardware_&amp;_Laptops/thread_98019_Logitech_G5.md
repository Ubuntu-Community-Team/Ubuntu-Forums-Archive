---
title: "Logitech G5"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by cdgore on 2005-12-02
Hi.  I just got a [Logitech G5 mouse]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2142,CONTENTID=10715").  It's great, but I can't figure out how to get the tilt wheel to work.  When using evdev as the "Protocol" in my xorg.conf, the tilting ends up mapping to whatever the scroll wheel is.  If anyone has figured out how to get the G5 to work, I'd really appreciate some help.

---

### Post by cdgore on 2005-12-03
Nevermind.  I got it to work using this configuration in my "InputDevice" section:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Gaming Mouse"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
        Option          "Resolution"            "2000"
EndSection

---

### Post by Maddy on 2007-12-27
Thank you!

---

### Post by drewsdesign on 2008-02-26
cheers :)

---

