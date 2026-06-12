---
title: "ornico_usb compaq presario w200"
date: 2012-02-27
forum: Hardware
---

### Post by smkatz on 2012-02-27
Hi. I am running lubunttu 11.04 on a Compaq EVO 610c. The Ubuntu instructions ([https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200))  for installing this driver on the wiki seem old compared to this one:
[http://wiki.debian.org/orinoco_usb](http://wiki.debian.org/orinoco_usb)

Can I use these instructions to make this chipset work including WPA support?

Thanks for your help.

--Sam

---

### Post by gordintoronto on 2012-02-27
I suggest the latest version of Ubuntu. It has built-in support for several WiFi adapters which are not in 11.04.

---

### Post by smkatz on 2012-02-27
Would lubuntu 12.04 work, or does lubuntu lag behind the latest release? I'm actually running 11.10, actually not 11.04?

I only have 256MB of RAM which is why Lubuntu was recommended to me. The Ubuntu livecd wouldn't boot (it gave no error message, it just tried and eventually booted into windows). It did make a weird sound.

Lubuntu did boot.

---

### Post by smkatz on 2012-02-27
My diagnosis is my client never had the module installed. It's unclear whether it's PCMIA or USB but here it is:
[http://h20331.www2.hp.com/hpsub/cache/311483-0-0-225-121.html](http://h20331.www2.hp.com/hpsub/cache/311483-0-0-225-121.html)

And here is the driver in case anyone wants it:
[http://www.nongnu.org/orinoco/](http://www.nongnu.org/orinoco/)

I also found instructions for Redhat, but don't think those are relevant.

---

### Post by gordintoronto on 2012-02-27
Lubuntu does not lag behind.

From the spec page you linked to:
"Interface USB 2.0 compliant, backward compatible with USB 1.1"

The latest update to the driver was six years ago. I suggest laying out $20 for a supported USB WiFi adapter. Plug it in, "it just works."

---

