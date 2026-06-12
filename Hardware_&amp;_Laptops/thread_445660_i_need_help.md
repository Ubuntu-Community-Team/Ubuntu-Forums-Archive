---
title: "i need help"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by mbakar on 2007-05-16
cannot install acer travelmate 2480 audio driver, display and network drivers. could please help me out

---

### Post by teaker1s on 2007-05-16
firstly if you get just a terminal login or blank screen
reboot
at boot grub menu (you may need escape key)
select recovery kernel
type
sudo dpkg-reconfigure xserver-xorg
follow the prompts and for a driver select "vesa" reboot and lets see if you have gui

---

