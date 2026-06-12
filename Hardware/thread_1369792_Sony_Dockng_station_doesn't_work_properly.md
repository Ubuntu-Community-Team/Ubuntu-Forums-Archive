---
title: "Sony Dockng station doesn't work properly"
date: 2010-01-01
forum: Hardware
---

### Post by bgrohe on 2010-01-01
I have a sony vaio PCG-XG500. It came with a sony dock PCGA-PSX1. The usb ports work, but the composite video input doesn't. Is there a driver i need to install or something?

---

### Post by webbdawg on 2010-01-01
I have a sony sz330p with a sony docking station. It took me a while to figure out.

If you have the Nvidia chipset make sure you have the Nvidia X Server installed.

After you get it installed go the Applications > System Settings > Nvidia X server settings and there you can get your second screen working.

---

### Post by bgrohe on 2010-01-01
I don't think that I have a Nvidia Chip set. when I use *lspci *without the dock in, I get 

[I]01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
[/I]
Should I still treat it as a NVIDIA chip set?
I also don't wan't a second  screen, I want to have video imported.

---

