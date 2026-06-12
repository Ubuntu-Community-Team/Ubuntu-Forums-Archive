---
title: "Installation Won't Boot"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Pk023 on 2009-08-26
I have tried everything many times. I am trying to install Ubuntu 9.04 on my PC (64 bit Vista with Intel 2.5 Pentium Dual Core and NVIDIA Geforce 9600), so I go to the boot menu and start Ubuntu, then it shows the loading screen, where it says Ubuntu, then it loads tons of stuff and everything says [ OK on the right side of the screen, then it stops at "* Starting bluetooth" and stays there for about 15 minutes then the screen goes black and does nothing. Does anyone know why this is happening?

---

### Post by ajgreeny on 2009-08-26
Is this in your actual installed version or the live CD?  Normally the installed version and also the live CD show a splash screen on bootup, not all the scrolling text that you describe.  Perhaps you have disabled usplash on purpose to see why the system will not boot.

However, it is bluetooth that is causing the problem it seems, but if you can not even boot into the system, I'm not sure where to go from here, other than a reinstall, or you could try booting to the recovery mode and for the time being at least uninstalling bluetooth. So choose recovery mode from the grub menu, then choose command line, and then ```
apt-get remove bluetooth
```I don't think you need the sudo in front of the command in recovery mode but if it does not work without it try with sudo in front.  Then try ```
startx
``` or if that does not work ```
reboot
```You can then try to add bluetooth again if you are going to need it, or just leave it out of the system.

---

### Post by Pk023 on 2009-08-26
Well, it shows the screen that says Ubuntu and the bar loading, after it is done, it does the scrolling text screen and stops.

---

