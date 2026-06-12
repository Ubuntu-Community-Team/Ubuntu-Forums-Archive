---
title: "Live-CD 5.04 i386: system hangs on &quot;configuring graphics hardware&quot;."
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by mike_esper on 2005-08-31
I am unable to boot Ubuntu 5.04 Live-CD beyond "**configuring graphics hardware**" as detailed below. Any help would be appreciated.

My computer specs:
Pentium-3 @ 450 Mhz
128 MB RAM
**Diamond Stealth S220 video card** (chip: **Rendition** (v2100 listed as driver in Windows 2000)(note: via some googling, supposedly this card works in Linux if you use the "Rendition" driver--see below)

Notes: 

1) the Ubuntu CD-RW I burned is functional. I tested it on another computer and there was no problem booting completely into Ubuntu.

2) I tried a SLAX Linux Live-CD and it worked fine on my computer, although the monitor refresh rate was low (72 hz I think - and that was the only option on the menu). I'm pretty sure it was running at 1024x768 but I didn't write it down.

3) Under Windows 2000 the video card settings match what Ubuntu reports: pci bus 0, device 20, function 0.


My attempts to boot Ubuntu were as follows:

#1: normal boot (just pressing enter): system hangs (i.e. just sits there with no change) at "**Preparing for live session - configuring graphics hardware - 73% on progress bar**". I waited 5 minutes with no change.

#2: tried using "live noapic nolapic" command. Result: hangs at the same spot as before.

#3: tried "live-expert" mode: chose "autodetect video = yes", chose "Rendition" under later menu, then "v2000/v2100/v2200" under menu; kernel framebuffer = yes. Result: hangs at the same spot as before.

#4: as in #3 except chose "autodetect: no", driver: "vga" and "generic video card" under menus, framebuffer: no. Same result.


Questions:

1) Are there are workarounds or solutions to this problem? (aside from the obvious of using a different video card - another post in this forum suggested buying an old used video card that is known to work in Linux)

2) Would the Install-CD (i.e. not Live-CD) have the same result? I did not try this because I want to backup my data before tinkering with partitions.

Thanks.

---

### Post by blueshrike on 2005-09-11
I have a similar problem.   Only I wiped out my current debian installation to install ubuntu so I was performing a real installation.  Not using the live CD.

I have an ASUS CUSLC2-C PIII Mobo with a diamond stealth II S220 video card.

Essentially, it gets to the point where it attempts to configure the XServer and then it hangs. 

I assume that ubuntu does not support the Diamond stealth II video card out of the box.  I  would also appreciate any suggestions on this matter.

---

### Post by blueshrike on 2005-10-04
I checked out x.org.  It seems as though there is little support for that kind of card.  So I bought a used ATI Rage card.  And it works fine.

---

