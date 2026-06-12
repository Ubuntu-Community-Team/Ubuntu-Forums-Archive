---
title: "DiNovo Edge Bluetooth"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by alawson on 2009-10-06
Hi all,

Sorry I've done a bit of searching, but am unable to find any definitive info on this subject for Jaunty.

I just bought myself a Logitech DiNovo Edge keyboard with integrated touchpad mouse.

It works pretty well as a bluetooth keyboard as long as I don't use the supplied dongle. I had an Asus bluetooth USB adapter kicking about from something else, and it's working fine through that as I type.

I have a few troubles tho.

At seemingly random intervals the touchpad stops working. Sometimes it wakes up, sometimes it doesn't. I need some tools to debug what's going on....

Is there a simple way of listing the currently attached bluetooth devices from the CLI?

I can do the following;
```
$ hcitool dev
Devices:
	hci0	00:02:72:xx:xx:xx

```

but that isn't the keyboard's MAC as listed on the reverse, which starts 00:07:61

Any other way to list this stuff out?

Thanks for your help!

---

