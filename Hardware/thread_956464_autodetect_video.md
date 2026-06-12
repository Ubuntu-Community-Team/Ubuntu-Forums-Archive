---
title: "autodetect video"
date: 2008-10-23
forum: Hardware
---

### Post by lucas_a on 2008-10-23
since i have ubuntu installed on a usb pendrive, i take it with me everywhere, and im using lots of computer and i have to be downloading and installing, uninstalling drivers for different computer (xorg drivers) so i wanted to know if there is any way to have them all (all most common drivers) already installed on ubuntu and let it choose at boot time which video driver it should load automatically?

Ive been searching trough the internet, irc, and no one there knew howto do this.... I hope some one here can give me a hand...

thanks for reading this, ill appreciate any help...

---

### Post by prshah on 2008-10-23
> **lucas_a said:**
> since i have ubuntu installed on a usb pendrive, installing, uninstalling drivers for different computer (xorg drivers) 

First of all, Ubuntu does not used a "cached" driver model, like XP. Most drivers are loaded at startup after autodetecting the hardware. This is why Ubuntu (and most linuxes) work fine even after changing critical hardware such as the motherboard / HDD.

Secondly, you call install all available display drivers using ```
sudo apt-get install xserver-xorg-video*
``` but this will take up a hefty bit of space, and you need "session persistance" on your pendrive ubuntu install. You should normally be using only the VESA driver, which will work on all (practically) graphics cards.

Except for display drivers, you should not require drivers for most hardware.

Wireless and Modem are important exceptions; installing ndiswrapper to your session-persistant-ubuntu-pendrive should get over that hurdle; Since most systems will have Windows using their wireless drivers will enable wireless on your ubuntu-off-pendrive-live session.

---

