---
title: "Ubuntu on ViewSonic VOT132 computer"
date: 2021-10-20
forum: Hardware
---

### Post by stevermann on 2021-10-20
I bought a ViewSonic VOT132 computer to use as an NAS on my home computer.  It cost $40 and runs Ubuntu 20.04 just fine.  It's a bit slow, but for my purposes of file sharing between PC's on my local network, it works just fine.

If there is a power failure longer than my UPS can handle, the Sonic does reboot when power comes back on. But the boot freezes at the POST with a CMOS failure; the date and time is not saved.

Here's my problem. The Sonic and other servers in my home are in the basement and running headless.  There is no monitor or keyboard to "hit f2 to accept defaults and continue".  I have examined every square inch of both sides of the motherboard, and I can't find anything that resembles a CMOS battery.

I know this isn't something that Ubuntu can fix since it's the BIOS that's stopping the boot. But I am hoping that someone else may be familiar with this board and know where is the CMOS battery?

---

### Post by dougdeep2 on 2021-10-29
I believe your VOT132 is the same thing as a Foxconn nt-A3500.  It has the same specifications and the same crappy users manual.  Foxconn pulled most of their online support web pages but I saw a post in an AVS forum about the CMOS battery being on the underside of the main board.  The post was for someone that had goofed up a BIOS upgrade but they said to look for jumper posts (or maybe just solder pads) marked "clear" and the battery should be nearby.  The battery could also be hiding under another part like the WIFI card, speaker or a SIMM.

---

