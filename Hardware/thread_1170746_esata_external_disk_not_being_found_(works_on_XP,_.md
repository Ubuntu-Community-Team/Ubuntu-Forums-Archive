---
title: "esata external disk not being found (works on XP, gah!)"
date: 2009-05-26
forum: Hardware
---

### Post by javahollic on 2009-05-26
Hi,
I just got a shiny new Verbatim 2TB raid esata box : [[http://www.play.com/PC/PCs/4-/9564816/Verbatim-2TB-RAID-Extrernal-USB2-0-eSATA-Hard-Drive-Enclosure/Product.html]](http://www.play.com/PC/PCs/4-/9564816/Verbatim-2TB-RAID-Extrernal-USB2-0-eSATA-Hard-Drive-Enclosure/Product.html]), is detected fine under windowsXP (which I used _just_ to test it worked when 'buntu failed me!), but not so much as /var/log/messages chatter on esata connection/powerup.

Anyone confirm eSATA support supports hotplug configuration? Is it just me (again!)?

Had the problem on 8.10, have since upgraded to 9.04, same results.

dmesg attached

---

### Post by windfix on 2010-04-08
I just bought this same RAID box, assuming I'd at least get USB connectivity under Karmic.  No joy.  When plugged in to USB, here is output of LSUSB:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 18a5:0219  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 0c45:6300 Microdia 
Bus 001 Device 010: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 009: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 007: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 001 Device 006: ID 0c45:63f8 Microdia 
Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 009: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 008: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 007: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Anyone have suggestions?

---

### Post by windfix on 2010-04-09
First, the drive was unformatted.  From XP's "Manage Computer" (right click on My Computer) I was able to find the RAID and format it.  It was plugged in by USB at the time.  BTW, formatting took 2.5 hours!

Additionally, I didn't realize that there are eSata settings in the BIOS.  Mine was enabled, but needed to be set to AHCI which, according to other posts, allows for hot plugging eSata drives. I don't know the distinctions in eSata settings, but it sounds like a good idea to have the drive connected and powered on prior to booting the OS anyway, to be on the safe side.

Now I can see the RAID drive from Ubuntu and use it via eSata.  Yay!  1 Terabyte mirrored for safekeeping videos of my daughter.

---

