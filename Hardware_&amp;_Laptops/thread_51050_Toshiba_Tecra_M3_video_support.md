---
title: "Toshiba Tecra M3: video support"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by mvor on 2005-07-22
Hi,

I have just tried to install Ubuntu Hoary on a Toshiba Tecra M3 and I have run into a problem that seems related to graphics device support.

Installation from CD was uneventful, being detected most of the devices present, including the Nvidia GeForce 6200. By default xorg is using the 'nv' driver. However, when starting a Gnome session, the panel showing Gnome loading process does not appear, but the welcome tune can be heard. The usual Gnome panels do not appear (no taskbar, no menubar, etc.) and the keyboard seems to be blocked (I am unable of switching to a console by pressing Alt+F1, etc.). Alt+Ctrl+Backspace does not have any apparent effect either. Surprisingly enough, the mouse pointer can be moved, but after a minute or so, even that freezes.

I installed the official NVIDIA drivers (76.67) and the only thing it achieved was to froze the X server on startup (blank screen, the nvidia logo does not appear).

I then tried to use the vesa drivers. With this I got some more progress: the Gnome loading panel appeared, but then it froze when setting up the taskbar and menubar panels. Behavior was identical to the one I got with the 'nv' driver.

These effects have been replicated both with Ubuntu official kernel images 2.6.10-5 and 2.6.11-1. Disabling apic features by issuing kernel parameters did not have any visible effect.

Does somebody have a clue of what could be the problem? I think that the built-in fb support in the kernel could the culprit... 

Thanks, 

mvor.

PS: There are reports of a guy achieving to install FC3 and FC4 on a Tecra M3, with kernel 2.6.11. I will try to ask him to lend me his kernel config so I can try to build the kernel myself with his options.

---

### Post by mvor on 2005-07-24
I've managed to get it working by:

+ booting the system with ubuntu's kernel image 2.6.10-5
+ in /etc/X11/xorg.conf, the device was configured as follows:

Section "Device"
    Identifier      "<The string that ubuntu installer sets up>"
    Driver          "nv"
    BusID           "PCI:1:0:0"
    Option         "NoAccel"    "true"
EndSection

no other tweaking was made either to the kernel itself nor config files.

mvor.

---

