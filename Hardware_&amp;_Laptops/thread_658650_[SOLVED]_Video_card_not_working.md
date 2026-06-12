---
title: "[SOLVED] Video card not working?"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by zhimsel on 2008-01-04
This is not exactly Ubuntu related, but I figured you guys might be able to help (or at least tell me where to go).

I used to have my PC in a milk crate (see [http://ubuntuforums.org/showthread.php?t=654791](http://ubuntuforums.org/showthread.php?t=654791)). I just got a new case and got all the parts installed. Somewhere in the transfer, something happened, because my system will not display video. 

Here's what I have concluded so far:


1. It's not a DVI cable problem, as all 4 cables don't work. And 2 are brand new. 

2. It's not a monitor problem. I tried using 2 different monitors, and neither work, but they both work on another PC.

3. It's possibly a motherboard problem. Normally when you boot a PC, until the boot process gets handed over to the OS from the BIOS, a single toggle will turn off the PC, but once the OS starts loading you have to hold it to turn off. When I turn on my comp, even if I leave it on for 10 min, a single toggle will shut it off. This leads me to believe that the boot process is getting stuck at the BIOS loading (with an error or something), so GRUB never even starts. 

4. It's obviously a possible video card problem, but I'm not certain.

Other misc. facts:

1. If I take a DVI to VGA converter and plug the monitor into the video card, I get garblely-gook (probably the digital signal being displayed in analog). But there is just no signal when strait DVI is used.

2. I tried resetting the BIOS/CMOS by following the manual (not sure if it worked as I can't see any results), figuring maybe there was a BIOS setting that is resposible.



System Specs:

Motherboard: Asus M2N-SLI Deluxe (nForce 520MCP Chipset)
Graphics: Asus ATI Radeo X800
CPU: AMD Athlon 64 LE-1600 (2.2GHz)
RAM: 2GB OCZ DDR2 800 (These are manually set to 2.1V in the BIOS)
Monitor: Acer AL1916 (one of them)


Any help would be appreciated... Thanks!

---

### Post by overdrank on 2008-01-04
Hi and if you have been using the system in the milk create I would say reseat the video card. If  that does not work then remove the MB and bench test the system because the MB may be shorting in the case.

---

### Post by zhimsel on 2008-01-04
> **overdrank said:**
> Hi and if you have been using the system in the milk create I would say reseat the video card. If  that does not work then remove the MB and bench test the system because the MB may be shorting in the case.

I have reseated the video card numerous times. It overheated twice due to lack of contact between the heatsink and GPU core. I fixed that, but it may have something to do with that. 

I will bench test it tomorrow when I have the time, if not then Sunday. I will let you know the results.

---

### Post by zhimsel on 2008-01-06
> **zhimsel said:**
> I will bench test it tomorrow when I have the time, if not then Sunday. I will let you know the results.

I reseated everything, including the motherboard itself, to check for shorts. Still didn't work. I'm going to return my card and try another one. I'm hoping it's not my motherboard, as the RMA doesn't apply to open box items ='[

I'll let you know what happens.

---

### Post by zhimsel on 2008-01-13
It was the video card. I got another one and it fixed the problem... If only I could get my drivers switched over =]

---

