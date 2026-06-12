---
title: "Laptop Lid Switch Reversed? Turns screen gray and blank."
date: 2015-02-02
forum: Hardware
---

### Post by justananomaly on 2015-02-02
Mint 17.1 (Ubuntu 14.04)
Asus Q550LF laptop
Nvidia GT 745M + Intel HD 4400 (Hybrid)
Although this happens regardless of what version of nvidia driver i use, currently using latest nvidia 346 driver set (w/ nvidia-prime in nvidia mode although it does it in intel mode too) although again I have tried 331 and 343 as well.
1920x1080 resolution

Posted on the Mint forums and got no response, but I can confirm **it happens if I use stock Ubuntu 14.04 as well**, and seems to be an issue inherent with Ubuntu itself.

Doesn't matter which display manager I use, it seems to happen all around. I have tried lightdm, gdm, and mdm.


[LIST]
[*]When I have my laptop lid open between 80-100 degrees, the screen turns gray.
[*]If I close the laptop lid and quickly open it to +100 degrees and unlock it with my password, it runs properly.
[*]If i close the laptop lid and open it to between 80-100 degrees, the screen turns gray again.
[*]If I close the laptop lid and open it to under 80 degrees it unlocks fine, if I try to open it more it turns gray.
[*]When the screen is gray, switching to a TTY mode via my keyboard does not work.
[*]Power options for AC and Battery both set to "do nothing".
[/LIST]

dmesg gives me following output for each instance the screen turns gray/blank.

```

ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
vgaarb: this pci device is not a vga device

```


I would just disable the lid switch in UPower, but for some reason sometimes firefox and chrome both make the screen go gray (when opening them or sometimes opening a new tab) no matter what angle I have the laptop lid open with, and closing it and reopening it are the only way I know how to recover without rebooting.

Is there a resolution to this, OR a script I could run with a keyboard shortcut to recover instead of having to close and open the lid so I can just use that?

---

### Post by justananomaly on 2015-02-02
Solved, it's not a software side issue, it's the LVDS cable inside the laptop. I will try reseating both ends.

---

