---
title: "Sound Problem"
date: 2008-08-01
forum: Hardware
---

### Post by Tools1100 on 2008-08-01
Does Anyone know how to fix this problem?


""The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.""

This is the message I get...

Toshiba Satellite
Intel Centrino 1.7
Built in sound card

Other error messages:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by opscure on 2008-08-01
Here's a troubleshooting guide that should help:
[http://ubuntu.sabza.org/2007/05/07/troubleshooting-volume-and-sound-card-configuration-in-debian/](http://ubuntu.sabza.org/2007/05/07/troubleshooting-volume-and-sound-card-configuration-in-debian/)

---

### Post by evets25 on 2008-08-01
It sounds like your sound card is not being detected/has no driver.

---

### Post by Tools1100 on 2008-08-01
> **opscure said:**
> Here's a troubleshooting guide that should help:
[http://ubuntu.sabza.org/2007/05/07/troubleshooting-volume-and-sound-card-configuration-in-debian/](http://ubuntu.sabza.org/2007/05/07/troubleshooting-volume-and-sound-card-configuration-in-debian/)

That didn't fix it... I'm still getting this error message:

"No volume control GStreamer plugins and/or devices found"

Linux is new to me so I'm not up on the linux commands...

---

### Post by ginbas on 2008-08-01
Sounds like the driver "module" for your sound adaptor hasn't been enabled in your kernel. Check out how to compile an ubuntu kernel and add your sound card harware. **I'm new so don't get pissed if I'm wrong.**

---

### Post by Tools1100 on 2008-08-01
Ok... I'm a bum As* some how I installed linux-image-2.6.24-9 server...

Linux kernel image for version 2.6.24 on x86/x86_64 

I uninstalled it and it fixed the problem....

Well maybe by telling you what I did it can help out someone with the same problem... Thanks for all the help people!

---

