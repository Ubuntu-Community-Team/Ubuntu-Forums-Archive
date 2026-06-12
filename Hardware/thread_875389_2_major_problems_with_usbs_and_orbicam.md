---
title: "2 major problems with usbs and orbicam"
date: 2008-07-30
forum: Hardware
---

### Post by chimy100 on 2008-07-30
I have an acer aspire 5672 and ubuntu is the only os I have on it right now.  Currently, ubuntu is unable to find anything attached via usb except for a mouse.  My orbicam does not work, and as a noob, I haven't been able to find any way of making it work.  I just installed ubuntu today and it is up to date so I don't know what to make of it.  My usb drives are working because my external will turn on when plugged in, however ubuntu doesn't recognize it:

lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Neither my orbicam or my external are acknowledged.

---

### Post by FredWiersma on 2008-08-21
I've just installed Ubuntu 8.04 on my Acer Aspire 9300. The Orbicam works with the application cheese, but so far not with the IM client pidgin.

In cheese I can make a photo, but not record a video.

If in a shell I type lsusb, I get:

Bus 002 Device 003: ID 5986:0100 Bison Acer OrbiCam
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 001 Device 001: ID 0000:0000

Anyone knows how to get to use my webcam in pidgin, or another IM client that's compatible with MSN?

Thanks!

---

### Post by FredWiersma on 2008-08-23
I'm now using aMSN as client, and thewebcam works! :popcorn:

Now the sound isn't working :(

---

