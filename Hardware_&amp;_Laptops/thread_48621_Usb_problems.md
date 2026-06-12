---
title: "Usb problems"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by Skerit on 2005-07-13
My usb stick will not mount ... It will nog show anywhere, not on /dev/sda and every piece of help on the internet assumes that it gets loaded there or somewhere else...

I installed a lot of usb stuff a while ago to try to get a webcamera to work, usbmgr and such, and when I did that my HAL stopped working in ubuntu and I had nothing, no sound, no network, ... so I deleted that, although I still have USBview and with that I can watch which deviced are on my usb ports... but that's all ... can't do anything now ... help please

---

### Post by torena on 2005-07-13
In a terminal session type "dmesg" and post here the contents please. :)

---

### Post by JonasR on 2005-07-13
I installed Ubuntu two days ago and initially noticed that though my USB mouse worked fine from the start, my USB memory stick did not seem to be recognised by the system. This is what got it working: I simply restarted my pc with the USB stick plugged in, which caused it to be mounted at start-up. Since then I can hotplug it, also if Ubuntu started up without the USB stick plugged in. 
So maybe a simple restart with the USB stick plugged in will solve it for you.

---

