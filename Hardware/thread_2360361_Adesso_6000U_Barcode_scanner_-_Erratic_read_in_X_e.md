---
title: "Adesso 6000U Barcode scanner - Erratic read in X environment"
date: 2017-05-03
forum: Hardware
---

### Post by velxundussa on 2017-05-03
Hello everyone,

I'm currently in the process of helping a small business to migrate their front-cash computers to Linux.
The great news is that 100% of the software they use is web-based so no hassle there, finding a driver for the label printer was simple and it even does a better job than on windows!

*nearly* everything works as intended!

But I'm breaking my head against the barcode scanner for some reason.

I'm installing the latest version of ubuntu gnome and the scanner in question is an "Adesso 6000U"

Like most scanners it actually emulates a keyboards that just types really fast.

The *weird* thing is that it works just fine in a tty, so I don't think this is related to a driver issue.
But when i try to scan anything in X it just enters gibberish.

Now I have a couple of ideas of where I may start looking but they all seem like non-starter:

- I know xorg has some configuration files that deal with keyboard, tough I read somewhere that Gnome overrule those 
- Gnome keyboard settings don't seem to let me set different keyboard mapping for different usb devices as opposed to xorg text config files

Any idea where I may go looking?

( I know a lsusb may be useful on this, but I don't have access to the computer in question at all time and don't have the output available know. I'm looking for a general direction on to where to go next time I have access to the computer )

Thanks a lot for your help!

---

