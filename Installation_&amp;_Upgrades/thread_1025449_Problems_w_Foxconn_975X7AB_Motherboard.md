---
title: "Problems w/ Foxconn 975X7AB Motherboard"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by ivanolo on 2008-12-30
Hello,

I've been using Ubuntu for a while now (since late 2006). I had never run into a problem I couldn't solve myself until I upgraded from a Socket A Sempron to a Core 2 Duo system based on the Foxconn 975X7AB motherboard.

The first snag I hit was caused by the infamous JMicron onboard controller. I had to pass the "all-generic-ide" and "irqpoll" arguments to the kernel when booting, in order for Gutsy to recognize my drives.

Even after flashing the BIOS to the latest version (635F1P33), ACPI has been extremely troublesome as well, thanks to Foxconn's highly-publicized, buggy ACPI implementation. Gutsy required a kernel parameter to force the use of ACPI. With Hardy, this is no longer necessary, but now my PC locks up randomly after logging into a GNOME session. The only solution I found was to disable ACPI both in the BIOS and in the kernel. This introduces yet another complication since I need to dual-boot, and Vista requires ACPI to work.

Before anybody asks, I checked the CD for defects; everything is fine. Memtest passed with flying colors, too.

Anyway, I'd like to get this resolved ASAP. Help me, Obi-Wan... err, guys, you're my only hope!

Here are my system specs.

Antec EarthWatts 380
Foxconn 975X7AB
Intel Core 2 Duo E6600
Arctic Cooling Alpine 7
3GB Kingston ValueRAM
ZOTAC GeForce 9600GT
LG DVD-ROM & DVD Burner
Sony FDD & Memory Card Reader
2x Seagate ST3160815A
2x Samsung HD753LJ

Thanks in advance.

---

### Post by ivanolo on 2008-12-30
Anybody?

---

