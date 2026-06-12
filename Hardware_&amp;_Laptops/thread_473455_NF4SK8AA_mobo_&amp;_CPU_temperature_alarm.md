---
title: "NF4SK8AA mobo &amp; CPU temperature alarm"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by desht on 2007-06-14
Hi all, here's a strange little problem I have with my Athlon 64 X2 on a Foxconn NF4SK8AA motherboard...

The system generally works just fine, other than a little problem that when the CPU temperature gets to about 45C, the temperature alarm siren on the motherboard starts sounding.  Now 45C isn't that hot for a Athlon X2 (should be OK up to about 70C), so I figured I could raise that alarm threshold in the BIOS.  The manual for the motherboard shows a "CPU Warning Temperature" setting in the "PC Health" screen.

But when I went into the BIOS setup, there was no such option!  There seems to be no way of raising the threshold.

Oddly, when I dual boot to Windows XP, I don't get the alarm siren even when the CPU is really busy & warm, so I suspect Windows is somehow altering the threshold itself.  No idea what it's doing though.

So, questions:

1) Anyone else got a NF4SK8AA mobo, and having similar problems?  If you do, is there a "CPU Warning Temperature" setting in your BIOS setup screen?

2) Anyone know how I might alter the warning threshold in Linux?  Some kind of ACPI setting maybe?

Thanks!

---

### Post by som4 on 2007-06-14
I have the same mobo and had the same problem.  You need to change the settings in the bios so that the fan starts up at a lower temperature.  That seemed to fix my problem in XP Vista and Ubuntu.

---

