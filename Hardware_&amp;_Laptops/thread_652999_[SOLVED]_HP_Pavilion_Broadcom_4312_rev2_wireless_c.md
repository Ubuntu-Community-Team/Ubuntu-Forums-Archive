---
title: "[SOLVED] HP Pavilion Broadcom 4312 rev2 wireless card"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by karl_kashofer on 2007-12-29
Hi all ! 

I try setting up a HP Pavilion dv6648eg notebook.
AMD Turion x2, nVidia Gforce 8400M GS, 

So far most things work, but I am struggling with the wireless card:

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1371
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at b0200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

Its not working with the bmc43xx driver, not with the b43 driver daily, not with ndiswrapper with the windows drivder from the ndiswrapper wiki (which seems to work for rev1). I cant find any windows driver on hp.com at least not for xp.

ndiswrapper:
beka@beka-laptop:~/driver/SP34152A$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

bcm43xx is blacklisted, but i still get no wireless device:
beka@beka-laptop:~/driver/SP34152A$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Anyone here who can help ?

thanks,
Karl

---

### Post by Dark_Stang on 2007-12-29
Did you load ndiswrapper?
```
sudo modprobe ndiswrapper
```
If that works you'll just have to add ndiswrapper to the modules list so it gets loaded on startup.
```
sude gedit /etc/modules
```

 I've been told that my drivers in the thread my sig links to work for a lot of the new broadcom cards. I'd give that one a shot if you don't think your driver is working.

---

### Post by karl_kashofer on 2007-12-29
Hi !

Thanks for the fast help !

It turns out it was actually a apic problem, i now just set "noapic nolapic" as kernel parameters and now it works!

Anyway thanks, I really like the spirit in here,
Cheers,
Karl

---

