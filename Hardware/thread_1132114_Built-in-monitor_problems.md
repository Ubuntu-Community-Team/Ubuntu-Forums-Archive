---
title: "Built-in-monitor problems"
date: 2009-04-21
forum: Hardware
---

### Post by Dramageek on 2009-04-21
Here's the situation: I'm trying to correctly configure Ubuntu 8.04 to run on a Javelin Viper POS System, the kind with the built-in touch screen. It has a VIA chipset, and ran WinXP before. For some reason, the built-in monitor won't work with (from what I can determine) X. Here's the boot sequence:
1. BIOS POST
2. Grub autoboot notice, etc.
3. Bunches of text.
4. Ubuntu splash screen with loading bar.
From here on out, only an external monitor through the VGA port works. (If I have it plugged in on boot, everything shows on both monitors.)

It did this on install, too. After a certain point I had to plug in a monitor to see what I was doing, but figured I could fix it after the install was finished.

xorg.conf was filled in by the install scripts with the default info, no driver specified, etc. Since it uses a VIA chipset, I specified the openchrome driver, and have tried the ActiveDevice options with that to no avail.

Another possibly related symptom: Using the alternate install CD, I get as far as the first menu (the one with the grey gradient in the background). Choosing ANY of the options gives me the text-screen loading display (loading i386/linux and i386/initrd.gz). After that clears, both monitors stay on, but everything is striped diagonally so that I can't read it.

Another symptom: Whenever I switch to any full-screen terminal (on shutdown, in another virtual terminal, etc.) the screen turns into a pink mess. 

Anybody have suggestions? I can post any logs that you need, just lemme know.

---

