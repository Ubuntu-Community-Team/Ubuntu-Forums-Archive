---
title: "Unable to boot to/access slave hard drive - can't access tty"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by The Wanlorn on 2007-08-07
The wires connecting my laptop screen to my laptop's base bit the big one and, instead of buying a new set of connectors, I decided just to pop my Ubuntu laptop harddrive into my WinXP desktop as a secondary harddrive.

I took the IDE cable from my CD drive and connected it to the laptop drive.  While XP recognizes that there is a drive connected to it, it doesn't give me a way to access it.  When I tried to boot from it, however, I get the following error:

```

/bin/sh: can't access tty; job control turned off
#
```

When I go from the root command line to the /usr/ directory, my username isn't in there.

Does anyone know how to get around this?  I really don't want to have to try to fix the wiring in my laptop, and I *definitely* don't want to lose my files.  Thank you!

---

### Post by BobCFC on 2007-08-07
It depends how many IDE drives you can have connected at once.  You could boot from the liveCD and copy the old linux data to a fat32 partition or an external USB drive, or over the network to a local to a samba share, or even upload the data to a gmail account if it just documents.

Or if it is an ext2/ext3 partition you could install a [driver in XP]("http://www.fs-driver.org/") to read linux partitions

Or you could shrink XP and install Ubuntu on your desktop in a dual boot, which you might want to do anyway since your laptop screen is dead.

---

