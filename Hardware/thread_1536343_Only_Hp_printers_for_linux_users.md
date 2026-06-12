---
title: "Only Hp printers for linux users ????"
date: 2010-07-22
forum: Hardware
---

### Post by sulekha on 2010-07-22
Hi all,

My friend is of the argument that he will buy only H.P printers, because of the HPLIP (Hewlett Packard
Linux Imaging project) where H.P developers work to make open source drivers available for linux and BSD.
This is probably the only instance where the device manufacturers works on fully free open sourced projects which support the full functionality (not  merely the just works bit)

 how correct is his argument ?
 does this mean that HP is the only Printer company that provides Linux driver support for its devices ?

 what about the epson associate avasys ([http://www.avasys.jp]("http://www.avasys.jp")) ?

 Is there any other company which provides similar support ?

---

### Post by psavva on 2010-07-22
> **sulekha said:**
> Hi all,

My friend is of the argument that he will buy only H.P printers, because of the HPLIP (Hewlett Packard
Linux Imaging project) where H.P developers work to make open source drivers available for linux and BSD.
This is probably the only instance where the device manufacturers works on fully free open sourced projects which support the full functionality (not  merely the just works bit)

 how correct is his argument ?
 does this mean that HP is the only Printer company that provides Linux driver support for its devices ?

 what about the epson associate avasys ([http://www.avasys.jp]("http://www.avasys.jp")) ?

 Is there any other company which provides similar support ?


Have a look here
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by PresenceofMind on 2010-07-22
I use HPLIP for my printers. I think HP themselves helped in the project as well and I find that this works the best with most of today's HP printers on Linux.

---

### Post by sulekha on 2010-07-24
> **PresenceofMind said:**
> I use HPLIP for my printers. I think HP themselves helped in the project as well and I find that this works the best with most of today's HP printers on Linux.


What about Nova 36 e vidar scanner ?

 Does anyone knows about any linux support for this scanner ???
 Their website doesn't mentions anything about linux
 [http://support.vidar.com/swcompatibility/default.htm](http://support.vidar.com/swcompatibility/default.htm)



[B]I think there should be a linux project which will produce a utility
very similar to ndiswrapper , so that we can use windows scanner
drivers for linux as well or in other words we can use win scanners in
linux as well [/B]

---

### Post by gradinaruvasile on 2010-07-24
Scanners are different.
There are some scanners (as do some printers) that work only in Windows via the GDI interface - they are designed this way. So dont buy GDI printers and stuff.
For a scanner to work in Linux, it has to be SANE compatible.

And most vendors dont bother to check their devices compatibility with Linux so missing a "Linux compatible" label doesnt say anything. Just try using xsane see if it works.

PS There are many printer drivers for Linux (mostly for PS/PCL printers). I used Konika Minoltas, Toshiba etc beside HPs from Ubuntu/Debian.

---

### Post by PresenceofMind on 2010-07-24
> **sulekha said:**
> What about Nova 36 e vidar scanner ?

 Does anyone knows about any linux support for this scanner ???
 Their website doesn't mentions anything about linux
 [http://support.vidar.com/swcompatibility/default.htm](http://support.vidar.com/swcompatibility/default.htm)



[B]I think there should be a linux project which will produce a utility
very similar to ndiswrapper , so that we can use windows scanner
drivers for linux as well or in other words we can use win scanners in
linux as well [/B]

Might work with the other scanner drivers that comes with Ubuntu. HPLIP is for HP printers and scanners.

---

