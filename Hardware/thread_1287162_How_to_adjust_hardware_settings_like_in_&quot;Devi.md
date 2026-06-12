---
title: "How to adjust hardware settings like in &quot;Device Manager&quot;?"
date: 2009-10-09
forum: Hardware
---

### Post by clevertomato on 2009-10-09
I wasn't sure whether to post this here or in "Networking." My example regards my Broadcom 4318 wireless G NIC on my Gateway MX7118 laptop, but my question applies to other devices, too.

In Windows, "Device Manage" shows drivers, driver versions, and, when appropriate, gives opportunity to change certain settings. For example, in the screenshot I can change many settings for my Broadcom wireless G, such as "Afterburner." How can I do this in Ubuntu for this NIC? How does one change settings for other devices in Ubuntu that would normally be in "Device Manager" in Windows?

---

### Post by Dark_Stang on 2009-10-09
Uhm... you don't typically do that for network cards, or most hardware for that matter. Is there a reason you're looking to do this? A certain feature you feel like you're missing?

---

### Post by clevertomato on 2009-10-09
In particular, I'm wondering how to enable "Afterburner" on my built-in Broadcom wireless NIC. I plan to get a router soon that supports the Afterburner feature, but I don't know how to enable this feature of my NIC in Ubuntu. It's obvious how to enable it in Windows. There must be a way to do it in Ubuntu.

I guess you're right that with most hardware devices, settings are not adjusted in Device Manager in windows. Besides the above NIC issue, I guess what I'm after is how to get information about devices and their drivers in Linux for use when troubleshooting, etc.

---

### Post by Dark_Stang on 2009-10-09
It appears to be on by default if your card supports it. Although you probably aren't going to notice the difference to be honest. 
[http://bcm-specs.sipsolutions.net/](http://bcm-specs.sipsolutions.net/)
[http://bcm-specs.sipsolutions.net/Afterburner](http://bcm-specs.sipsolutions.net/Afterburner)

Most of the hardware will just work with Linux. All of my hardware has support built into the kernel except for my Video card, because it's proprietary. If you're having issues with a certain peice of hardware you just need to find out exactly what it is. You can run "lspci" or "lsusb" to list all devices hooked up via PCI bus or USB. And from there you just need to do some research to make sure that your Kernel supports those devices. If it doesn't you just need to do a little research to see if there is a fix/driver available.

---

### Post by clevertomato on 2009-10-10
Thanks!

---

