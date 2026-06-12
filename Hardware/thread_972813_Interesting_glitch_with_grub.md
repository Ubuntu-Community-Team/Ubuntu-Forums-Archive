---
title: "Interesting glitch with grub?"
date: 2008-11-06
forum: Hardware
---

### Post by andre_orwell on 2008-11-06
This is just for feedback - no specific assistance requested.  :popcorn:

I've recently sorted a bit of an issue with grub on my Acer Aspire (5315-050508Mi).  I have ubuntu 8.10 installed on a USB drive and windows on the internal drive.  Grub is installed on the USB drive and I am able to get the bios to boot from the USB drive.  However for a while I was having some issues with Error 17.

Now, when I am running linux I can start grub and find /boot/grub/stage1.  This is a no-brainer as its only on one drive: hd1; hd0 has windows.

great... so I had done the usual root(hd1,0) setup(hd1) but kept getting error 17.  Eventually I tried twiddling the options at the grub prompt - tried root(hd0,0).  It booted just fine - huh?

Once the system was up and running I ran grub again just to check: usb drive is now hd1.

So somewhere along the line something is going pear shaped here.  I can boot my system but the configuration, for all intents and purposes, looks wrong.  Not sure if it is the bios or a grub bug (susspect bios on this cheapy lappy) but thought others might like to know (if there is a grub dev on the list?)

---

