---
title: "Ubuntu on Dell 630m"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by viraldhimar on 2005-12-09
Hi, I have recently purchased a Dell 630M, and I am having trouble installing linux on it. The graphics chipset Intel 915 (which I believe is the problem) is set to default 1280X800 in the BIOS and I can't change it. I have tried to force the live cd to run at 1024X768 and 800X600, but all I get is a blank screen after the modules are loaded. Is the solution going to be installing and then editing the xorg.conf file afterwards? I have run the gamut of live distros to see what works and would love to have Ubuntu work. Thanks for your help.

---

### Post by John.Michael.Kane on 2005-12-09
before you install at the boot promt type linux vga=792.

---

### Post by aysiu on 2005-12-09
[QUOTE=viraldhimar]Is the solution going to be installing and then editing the xorg.conf file afterwards?[/QUOTE] Yes, but to be on the safe side, maybe you should try editing the /etc/X11/xorg.conf on the live CD first. It'll create a temporary /etc/X11/xorg.conf. Once you play around with that and get one you like, you can save a copy and replace your installed xorg.conf with the temporary (and modified one).

---

### Post by Kolin S. Murray on 2006-11-30
Did we reach a consensus on how to do this? I'm not sure if I should install with the live CD or the alternate CD on the same system. Will installing with the alternate CD allow me to specify my resolution before I install?

---

