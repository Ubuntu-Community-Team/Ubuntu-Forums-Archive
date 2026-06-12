---
title: "ATI Radeon 4500 White Screen Problem"
date: 2012-07-15
forum: Hardware
---

### Post by billyauhk on 2012-07-15
Hi, recently my notebook have an issue. The monitor suddenly goes to pure white, and I cannot stop it. Sometimes it recovers after some tens of seconds, sometimes not. Today it even eats up my BIOS screen (the nice Toshiba logo). But it does respond to my keystroke (as I can tell by the HDD LED), and switching to virtual terminals (Ctrl+Alt+F1, say) will give me a blink, but I cannot take over the control as I do not know which process is causing the problem. Some other commands like "xset dpms force off" and changing backlit is still working while the screen is completely white.

This situation happens quite randomly for a week or so and I cannot figure any pattern. I have tried to turn off the GNOME effect, get into GNOME safe mode, re-install fglrx drivers, but it still comes without notice. Currently I decided to de-activate the fglrx driver and hope for the best. Here I want to know whether this is a known problem, caused by KVM, GNOME or the graphics driver.

My hardware configuration is:
Toshiba Satellite L500 with Ubuntu 11.04 64-bit
ATI related lines on lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730

---

