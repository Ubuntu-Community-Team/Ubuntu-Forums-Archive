---
title: "Gigabyte GA-970A-UD3, incompatible?"
date: 2013-10-04
forum: Hardware
---

### Post by benedikt2 on 2013-10-04
Hi there,

I recently bought a new PC and want to install kubuntu 13.04 (64bit) on it. Intallation finishes without a problem showing up. But the following hardware does not work:

- Not a single USB 2.0 port (but 3.0 does)
- WLan-Card gets stuck on "configuring network" and fails on it
- akasa cardreader-thingy including a bluetooth-connection

I think the motherboard is not fully supported, but cant find anything on the internet about it. Do you have any idea how to fix this? Strangely, the 32bit-version of kubuntu worked just fine (installed it by accident).

Here's my setup

```
AMD FX-8120 [COLOR=#666666]([/COLOR]8x3,5ghz[COLOR=#666666])[/COLOR]
8 GB Singlechannel ram
1 TB HD
60 GB SSD [COLOR=#666666]([/COLOR]50% windows/ 50% linux[COLOR=#666666])[/COLOR]
Gigabyte GA-970A-UD3 motherboard
Nvidia GTX 760 graphics
NET WLAN 150 Mbit PCIe Adapter [COLOR=#666666]([/COLOR]TL-WN781ND[COLOR=#666666])
[/COLOR]akasa cardreader-thingy including a bluetooth-connection
```

---

### Post by mörgæs on 2013-10-05
How does it work in a 64 bit install of 13.10?

---

### Post by benedikt2 on 2013-10-05
> **mörgæs said:**
> How does it work in a 64 bit install of 13.10?

Same problems. Installed all the updates it could find. This time it even found a propietary xorg-driver (or so), which is new.

PS: Added a nonworking part, forgot it

---

### Post by mörgæs on 2013-10-05
If you have the time it would be appreciated if you could create bug reports for the problems. 

Best is first to discuss with people in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") to see if the problems are known already.

---

### Post by klarglas on 2013-11-16
This guy, solved it by enabling IOMMU in Bios:

[http://www.skial.com/threads/having-trouble-dual-booting-win7-kubuntu.40410/](http://www.skial.com/threads/having-trouble-dual-booting-win7-kubuntu.40410/)

It worked for me, so why don't give it a try?

---

### Post by benedikt2 on 2013-11-19
Hey Glasklar,

worked just fine.

Thx for writing here and on ubuntuusers.de :)

---

