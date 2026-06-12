---
title: "Dell e1505 Touchpad Scroll not working"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by djkilgus on 2006-08-29
I just installed ubuntu and everything is working great with the exception of the scroll function on my touchpad.  I've tried firefox and open office and it appears that the problem is universal.  When I use the scroll, my cursor does change to the the "mini-scroll" suggesting that it does realize my intentions, but no scrolling occurs.  My apologies if this topic has already been discussed.  My searching has yielded no positive results.

Thanks!

As a side note, this is the only flavor of linux thus far that has given me my 1280x800 native 15.4 resolution.  I'm loving it already:-D

---

### Post by chuckao on 2006-09-01
Hi!

I have the same laptop and here the scroll works ubuntu dapper out-of-box.

But, only the vertical scroll works...the horizontal I don't have idea how I can put it to works.

Well, there is my touchpad section in /etc/X11/xorg.conf

Section "InputDevice"
   Identifier  "Synaptics Touchpad"
   Driver      "synaptics"
   Option       "SendCoreEvents" "true"
   Option       "Device" "/dev/psaux"
   Option       "Protocol" "auto-dev"
   Option       "HorizScrollDelta" "0"
EndSection

cheers

---

