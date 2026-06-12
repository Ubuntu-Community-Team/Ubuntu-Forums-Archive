---
title: "Canon Lide 220"
date: 2016-01-02
forum: Hardware
---

### Post by asearle on 2016-01-02
Hallo Everyone,

I am trying to install a Canon Lide 220 on a friend's Lubuntu 15.04 PC.  The scanner worked fine on my PC (Lubuntu 14.04) and seems to be physically present on hers as lsusb showed it.  But scanimage -L didn't find it.

I downloaded the new drivers following these instructions ...

<url>https://help.ubuntu.com/community/CompileSaneFromSource</url>

but couldn't find <quote>libsane-dll.so</quote> so couldn't follow through on the installation.

But I managed to compile/make everything following these instructions <url>http://mp610.blogspot.de/2008_04_01_archive.html</url>

... and replaced the rules file in /udev  and rebooted.

But the scanner is still not recognised.  Arrgghh!

When I ran <code>sane-find-scanner -v -v</code> I got ...

<code>found USB scanner (vendor=0x04a9 [Canon], product=0x190f [CanoScan], chip=GL848+) at libusb:003:003
could not open USB device 0x8087/0x0024 at 003:002: Access denied (insufficient permissions)</code>

But the current user is in the <quote>Scanners</quote> group and there doesn't seem to be any other authorisation setting not allocated.

I am a bit disappointed by all of this because, in the past, Linux has recognised most peripherals automatically.

Any tips would be most gratefully received.

Many thanks,
Alan

PS: In the Sane supported hardware listing Lide 220 is listed as having complete support

PPS: Would upgrading the PC to 15.10 help?

---

### Post by asearle on 2016-01-13
I fixed this problem by installing the SANE backends.  It was quite a tricky thing and I found the instructions on a german site.  If you have the same problem google around to find instructions.  But I'm a bit disappointed here that current/new drivers are not automatically included during updates or, alternatively, are installable via Synaptic.  Surely that would make sense?
Regards,
Alan

---

