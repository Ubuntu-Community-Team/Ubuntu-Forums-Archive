---
title: "Nvidia 9800 GT on 9.04?"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by Mythic_Commodore on 2009-09-22
Hey all. I have been trying to install 32-bit Jaunty in a dual-boot with my Vista Home Premium 64-bit and have been running into some problems getting graphics drivers to work. Basically my experience has been this cycle:

1. Install 9.04 from Live CD.
2. Run ndiswrapper to get my network adapter working.
3. Run update manager to get the system updated.
4. Download 185.18.36 Nvidia drivers from official website.
5. Install these drivers via console (Ctrl-Alt-F1, log into terminal as root, killall gdm, cd to download directory, install drivers from .run file, restart gdm).
6. Enjoy working Nvidia drivers.
7. Restart....computer decides to boot into low graphics mode with an error message about the kernel.
8. Run "dpgk-reconfigure -phigh xserver-xorg"
9. System is working again, but without Nvidia graphics.
10. Try to install Nvidia graphics (I suspect that it's changes to the xorg.conf that are not taking hold) trying the "nvidia-xconfig" command, which just brings the system back to the low display mode and forces me to run dpkg-reconfigure again, as well as attempting to install the driver via the Restricted Drivers window, which, oddly, will not display the driver at all until after I've installed it manually, at which point, the Restricted Hardware window recognizes it as available for installation.
11. After much playing around, I end up breaking the system eventually. It shows a black screen and blinking cursor instead of a login window and does not respond to any key commands.
12. Reinstall Ubuntu from Live CD and return to step 2.

Can anyone help me? Does anyone know of a good way to get these drivers installed? Is it because I am running a 32-bit OS on a 64-bit processor? Any answers would be much appreciated.

Hardware Specs:

Processor: Intel Core 2 Duo E4700 64-bit Dual Core @2.6GHz
RAM: 4GB (note that I was unable to assign a swap partition in my Ubuntu installation)
Graphics Card: XFX Nvidia 9800 GT
Ubuntu Hard Drive Partition: 20 GB ext3
Other OS: Windows Vista Home Premium 64-bit

Any answers would be very helpful. Thanks!
mythic

---

### Post by ks07 on 2009-09-22
Have you tried installing the nvidia drivers included in the restricted repository? It should work out of the box then.

---

### Post by Mythic_Commodore on 2009-09-26
Thanks for the help, ks07. I reinstalled Ubuntu, then ran ndiswrapper and restarted. After I restarted, I was able to locate the hardware drivers in the Restricted Drivers window without having to download them from the Nvidia website. The system worked great for a few days, but then inexplicably reverted the Appearance settings to the "None" effects level and began giving me this error saying that "Desktop effects could not be enabled" when I tried to fix it. Uninstalling and reinstalling the driver did not help. This did not occur after a restart - I was using my computer and it literally just instantly reverted to the normal appearance settings. Do you know what could have caused the system to just suddenly give up on me like that?


EDIT: This is solved for now....with emphasis on the "for now" part - I ran compiz-check (thanks Forlong!) and it said that another window manager was running, even though the Appearance window made it sound like a driver problem. I think that I had started metacity a few minutes before the effects reverted - I guess that did it. I just find it funny that the Appearance window didn't tell me that metacity was running instead and made it sound like a driver error, so I'm not going to mark this one down as solved just yet.

---

