---
title: "DVI (in)compatibilities"
date: 2009-04-09
forum: Hardware
---

### Post by dargaud on 2009-04-09
Hello all,
I have a new mobo that works perfectly with Ubuntu... except the DVI output of the onboard graphic card. I'm trying to figure out if it's a hardware problem or a BKAC problem.
Mobo is Asrock M3790GXH/128M with integrated AMD Radeon HD 3300 graphics. The onboard VGA plug works fine. The mobo works fine with my older DVI Nvidia PCI-X card. But I can't get anything out of the integrated DVI plug (during boot or later, so this is not Linux related, sorry if this is a bit off topic).

The Radeon HD 3300 has a DVI-D dual output and I tried it both with a DVI-D single and dual cable. My monitor is a DoubleSight DS-240WB and I cannot find the info if this monitor is dual or single link. And I have no idea if this is root of the problem.

The bios has an option for onboard, PCI-X and PCI graphic cards, which works for PCI-X (DVI and VGA) and onboard (for VGA). It also has an option for UMA and/or SIDEPORT which I cannot find enough info on, but anyway none of the options seem to work.

Anyway, I've had the mobo for 3 days and I have to decide _fast_ whether or not there's a problem with it to send it back.

Thanks a bunch.

---

### Post by askreet on 2009-04-09
Here's what I would do under those time constraints:

Install windows.

(waits for angry responses)

Seriously though, you can install XP and use the driver CD that's included.  If DVI still doesn't work, then the motherboard is broken.  If it does work then you have your work cut out for you to get it working in Linux.

Just a thought,
askreet

---

### Post by dargaud on 2009-04-10
> **askreet said:**
> Install windows
It's not a driver problem: I see nothing on the DVI port even during the BIOS or boot process. So either:
[LIST]
[*]it's a DVI incompatibility between DVI-D graphic card plug, DVI cable and DVI monitor. Is this even possible or is it always supposed to be compatible ?
[*]it's a misconfiguration of the BIOS (as I said I don't know what UMA and sideport are, and I've tried all combinations wothout success)
[*]it's a failure or the graphic card
[/LIST]
Help me pick one of those...

---

### Post by j85wilson on 2009-04-25
Are you certain that your monitor works?  Perhaps there is an issue of the card detecting the monitor (see Display Data Channel); if it thinks there is not a monitor there, then it won't send any output to that plug.  I suppose that a bit of bugginess in DDC stuff on either end might be regarded as a card <-> monitor incompatibility, but I would not call it that myself, just a bug.  Anyway, testing it with another monitor would be about the third thing I would try.

You could also try starting X with the monitor plugged in via DVI-D (just have to type blind), and then plug back in to VGA and look at the logs (/var/log/Xorg.0.log, for instance).  There should be a bit in there about whether or not it detects a display device on each output of your graphics card(s).

---

