---
title: "Firmware missing with new MPCI wireless card."
date: 2010-11-24
forum: Hardware
---

### Post by Tiz_earth on 2010-11-24
Before I begin, I'm going to tell you what it is I'm up to.

I've just put in a wireless MPCI card from a newer, junked HP Pavillion laptop into my 2002 HP Omnibook xe4400s.  The antenna came from a Gateway 400vtx junker, and is thrown in along the edge of the case where it can't be a nuisance.

I cannot currently send Internets through a series of tubes with this device.  When I click my top-bar network icon (as I would to select the wireless network to which I would like to connect) it tells me under Wireless Networks, "device not ready (firmware missing)"

So I run this, so nobody tells me to later: ```
lspci -v | less
```
...and the result:
> 00:09 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[INDENT]Subsystem:  Hewlett-Packard Company Broadcom 802.11b/g WLAN
Flags:  bus master, fast devsel, latency 64, IRQ 10
Memory at e0004000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb
[/INDENT]

Also, I tried booting from CD to see if the drivers just happened to have been left out or something when I installed Ubuntu.

What, forums, can I do about this?  I'm using 10.10 Maverick.

Not urgent or anything, but I figured it has to be less of a nuisance and faster than my USB Wifi card (which is stupidly faster than USB transfer rate)

---

### Post by Fafler on 2010-11-24
The Additional Drivers wizard should be able to install it, but personally i don't find the broadcom cards worth messing around with. Get a Intel 5100 instead.

---

### Post by pawhtiobo on 2010-11-24
You can always try the ndiswrapper to see if works.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

See ya...

---

### Post by Tiz_earth on 2010-11-24
> **Fafler said:**
> The Additional Drivers wizard should be able to install it, but personally i don't find the broadcom cards worth messing around with. Get a Intel 5100 instead.

The point is not to spend money.  If it ends up being a complete piece of junk, I'll eventually get another junk laptop that wasn't stripped of its goodies.  If I end up buying one, though, Intel 5100 is the one I'll get.  Thanks!

---

### Post by Fafler on 2010-11-25
Dude, it's $12 on eBay. You get 150 mbit instead of 54. It will connect to *any *accesspoint, not just those it feels like.  And it works properly with the opensource drivers already included.

---

### Post by Tiz_earth on 2010-11-25
> **Fafler said:**
> Dude, it's $12 on eBay. You get 150 mbit instead of 54. It will connect to *any *accesspoint, not just those it feels like.  And it works properly with the opensource drivers already included.

Well I'll see about buying it then, later, when this one leads me wrong.

---

### Post by Tiz_earth on 2010-11-25
Looks like I got it running.  I used the, "Additional drivers," feature under System > Administration and it recommended that I install the driver for it.  It works fine now.

---

