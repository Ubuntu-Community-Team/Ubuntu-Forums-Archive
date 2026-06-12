---
title: "Need help setting up Sidewinder AND Analog gamepads"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by BeauMN on 2006-11-30
I have two gameports, one on my onboard Trident soundcard and one on my PCI Sound Blaster Live 5.1.  I have an old analog gamepad hooked up to the onboard port, and a Microsoft Sidewinder gamepad hooked up to my SBLive.  They both work together in Windows2000 with no trouble, but I can't get them to work at the same time in Ubuntu Edgy (6.10)

If the 'analog' module is loaded, the sidewinder doesn't work.  (Ubuntu thinks it's an analog joystick, despite the sidewinder module being loaded)  If I remove the 'analog' module, then the sidewinder works, but the analog gamepad does not.

How can I get them both to work at the same time.  Is there a way to set things up so the 'analog' module only gets applied to one of the gameports/joysticks?

Thanks for your help!

---

### Post by BeauMN on 2006-12-03
Okay, I got them both working.  Here's how I did it in case anyone else is having this problem:

1. Open /etc/modprobe.d/isapnp
   Comment out the following line:
   alias pnp:dPNPb02f analog
2. Open /etc/modules
   Add the following (in this order!!):
   sidewinder
   analog

Reboot, and they should both work!

---

