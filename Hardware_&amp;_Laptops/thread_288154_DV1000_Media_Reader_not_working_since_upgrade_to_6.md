---
title: "DV1000 Media Reader not working since upgrade to 6.10"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Wheelman on 2006-10-29
Hey guys, I just upgraded to Ubuntu 6.1 from 6.06 the other day using the alternate install cd.  The upgrade went great and everything seems to be running good, but I noticed that since the upgrade my dv1000 doesn't recognize my sd card reader anymore.  On 6.06 i could just plug it in to the reader and it would pop up on the desktop.  Now when I plug it in the light blinks for a second and then nothing.  Any ideas? :confused:

Also: Noticed when i choose the previous kernel on the boot screen, it works fine.  The latest one (2.6.17-10-386 doesnt work) but the previous (2.6.15-27-386) works just fine.

How can I make it work under the newest kernel?

---

### Post by Wheelman on 2006-10-29
lspci -v output shown below:

> 06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 169
        Memory at b0104000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2

06:09.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 169
        Memory at b0108400 (32-bit, non-prefetchable) [size=256]
        Memory at b0108000 (32-bit, non-prefetchable) [size=256]
        Memory at b0106400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2


---

### Post by togume on 2006-11-02
I can attest that it does not work with Edgy, fresh install, on a DV1000.

As you said, the media reader light - lights up for a second, then nothing happens. 

Any ideas are welcome!

---

### Post by JoeSchmoe1971 on 2007-01-25
I have two dv1000 laptops, one still runs windows xp home and has a faster processor, one is slightly older and does not. The older one with Ubuntu is running 6.06 and the card reader works fine, but not with all cards. Anything larger than 1GB sometimes does not work. The newer laptop that still runs on windows can read any card I put into it. 

The only thing I can think of is that the newer laptop might have a card reader with a BIOS that accepts larger SD cards, while the older one does not.  Not all of the older card readers can read big SD cards. Then again, the same laptop used to read a 256k memory stick pro when it was running XP home, but now it cannot read that same memory stick. Very weird. 

Hope this helps

---

