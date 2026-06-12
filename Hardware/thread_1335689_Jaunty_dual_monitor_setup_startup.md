---
title: "Jaunty dual monitor setup startup"
date: 2009-11-23
forum: Hardware
---

### Post by Esthellin on 2009-11-23
I am using Ubuntu Jaunty (not game enough to upgrade to Karmic befor the first update release :P) and I am attempting to get dual monitors working. My laptop is a Toshiba and the other monitor is a LG Flatron L1719S.
Connecting the monitor when the laptop is already on and signed works fine (turning it on through gnome-display-properties).

Rebooting the computer gives very odd behaviour:
The output of the startup screen (such as the bootloader and splash image) are all on the external screen rather than the main laptop screen.
Gdm fails. As soon as it is about to start, both screens go blank and I have to restart the laptop.

I have attempted disabling gdm, doing a text login then and running "sudo /etc/init.d/gdm start" to start gdm separately. This gives inconsistent errors. Sometimes the text login will load on the laptop screen, other times on the external monitor. Also, sometimes gdm works, but others it fails like before.

Note: The laptop and external monitor screen's resolutions are different. Laptop:1280x800.I don't know the external's resolution; the settings available show different numbers depending on the weather :(. The most usual one is 1024x768.
Other Note: My graphics card is NVIDIA.

EDIT: I looked up the external screen, and the maximum resolution available for it is 1280x1024, an option not available when I connect it to the laptop. I had a look and found that on 1024x768, a small section of the right and bottom edge of the screen is "chopped off". I think this would be due to the incorrect screen resolution ratio.

---

### Post by Esthellin on 2009-11-25
> **Esthellin said:**
> I am using Ubuntu Jaunty (not game enough to upgrade to Karmic befor the first update release :P) and I am attempting to get dual monitors working. My laptop is a Toshiba and the other monitor is a LG Flatron L1719S.
Connecting the monitor when the laptop is already on and signed works fine (turning it on through gnome-display-properties).

Rebooting the computer gives very odd behaviour:
The output of the startup screen (such as the bootloader and splash image) are all on the external screen rather than the main laptop screen.
Gdm fails. As soon as it is about to start, both screens go blank and I have to restart the laptop.

I have attempted disabling gdm, doing a text login then and running "sudo /etc/init.d/gdm start" to start gdm separately. This gives inconsistent errors. Sometimes the text login will load on the laptop screen, other times on the external monitor. Also, sometimes gdm works, but others it fails like before.

Note: The laptop and external monitor screen's resolutions are different. Laptop:1280x800.I don't know the external's resolution; the settings available show different numbers depending on the weather :(. The most usual one is 1024x768.
Other Note: My graphics card is NVIDIA.

EDIT: I looked up the external screen, and the maximum resolution available for it is 1280x1024, an option not available when I connect it to the laptop. I had a look and found that on 1024x768, a small section of the right and bottom edge of the screen is "chopped off". I think this would be due to the incorrect screen resolution ratio.

Well it looks like I have fixed it. I installed the extra drivers for the NVIDIA graphics card, used the nvidia-settings to setup the extra monitor with Twin-View, then saved the configuration in the xorg file.
I don't know why the bootloader appears on the external monitor, but everything starting from gdm works now :D

---

