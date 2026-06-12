---
title: "Question(s) regarding Belkin F7D1101 v1 Basic Wireless Adapter"
date: 2014-03-23
forum: Hardware
---

### Post by scollar1971 on 2014-03-23
I am the owner (not so proud) of a Belkin Wireless Adapter and looking for a answer to what I feel should be simple question (I guess that makes me sound foolish)

lsusb displays

```
sean@sean-Dimension-4700:~$ lsusb
Bus 001 Device 004: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]

```

Label on device shows f9l1001v1 Is that false advertisement or is lsusb wrong?

---

### Post by scollar1971 on 2014-03-23
This is what script generates

[http://pastebin.ubuntu.com/7140994/](http://pastebin.ubuntu.com/7140994/)

And now this probably going the suggest moving this thread and I am perfectly good with that

My next question is regarding the optimal driver for this chipset?

What should I be using?

---

### Post by chili555 on 2014-03-23
The terminal command *lsusb* doesn't read the cardboard box; it doesn't read the sticker on the device; it reads the details hardcoded into the silicon chip. I suspect that Belkin may have added some trivial software feature to their CD and called it an F9L1001v1 instead of the previous F7D1101v1. I also suspect they charged another few dollars for it.

The working reasonably well driver for that usb.id 050d:945a in recent versions of Ubuntu is *r8712u*. There is an experimental driver available called r*92su*. Whether it works any better or offers any feature not available in *r8712u*, I can't say; first, I haven't the device and, second, I haven't yet worked on any case where the poster reported that some problem was remedied by installing *r92su*.

---

### Post by scollar1971 on 2014-03-23
As always thank you chili555 I know we have discussed before and you've been very helpful I'm searching  to see if it is beneficial before I attempt it again.
 
Has anyone here used this driver[COLOR=#000000] r[/COLOR]*92su *with success?

---

