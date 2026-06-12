---
title: "Ubuntu 18 on RCA Cambio"
date: 2018-05-25
forum: Hardware
---

### Post by ethanweegee on 2018-05-25
I tried Ubuntu 1**7**.04 on my RCA Cambio before. It's a Baytrail IIRC, has a 32 bit UEFI, and it was a nightmare. Sound didn't work, touch didn't work, it was stuck in portrait, wouldn't go landscape. I had to use nomodeset since, without it, the display would be a garbled mess. Bluetooth didn't work, although I did manage to get Wi-Fi working. And this was with isorespin.sh. It just felt cumbersome getting it working, so I gave up.

Fast forward to Ubuntu 18. I tried again. This time, it booted fine after isorespin.sh (Didn't try booting without it). To my surprise, it started in landscape! (By that I mean, everything past the Ubuntu boot screen was landscape) I discovered rotation worked, although the portrait mode was upside-down. That can be fixed later. Wi-Fi works out of the box, but refuses to connect to my network. Not entirely sure why, but I'll test connecting to Windows 10's mobile hotspot later. Bluetooth still doesn't work, the touch screen still doesn't work. Sound doesn't work, but it does detect the sound, while Ubuntu 16 listed "Dummy output" instead. The volume keys cause the volume icon to disappear, and there is no slider pop up, which is strange. Does that mean the driver doesn't work with the sound device? I'll be trying headphones later as well.

So my question is; has anyone else tried this? Anyone gotten this tablet (or a similar one) to work? Or, any suggestions to fix the problem?
I'm also running this all from a (persistent) live USB install. Will installing it to the tablet fix anything?

EDIT: Wi-Fi is working.

---

