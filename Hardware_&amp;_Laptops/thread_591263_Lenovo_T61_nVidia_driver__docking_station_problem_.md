---
title: "Lenovo T61: nVidia driver / docking station problem on Gutsy"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by grmbrand on 2007-10-25
System setup:
Lenovo T61 w/ nVidia Quadro 140M
Docking Station
Samsung SyncMaster 226bw LCD monitor, DVI connector to docking station

Problem:
If I use the non-restricted video driver: I can put the laptop in the docking station, power it up without opening it, and the external monitor displays the desktop correctly.

If I use the restricted nvidia driver, the desktop is not forwarded to the external monitor - but when I flip open the laptop, the desktop appears on the laptop monitor correctly.

Is there a system setting that I'm missing, or is this a driver issue?

Before you tell me to assign the external monitor as Screen 2, note that when the laptop is in the dock, the external monitor is technically Screen 1. The only way to address  it as screen 2 would be to physically connect it to the second monitor hookup, which is not replicated on the dock.

Any ideas?

Cheers,
Grmbrand

---

### Post by pwhite on 2007-11-12
Grmbrand,

Thanks for motivating me to give this another shot. I have a T61 with nvidia graphics as well, and I was finally able to get everything working by using the restricted driver manager, and then running sudo nvidia-settings where I **disabled** the internal LCD display and configured my external Samsung SyncMaster 204B. Once I did that and restarted, everything works like a champ. :)

I hope this helps,
Peter

---

### Post by syxbit on 2007-11-17
in the bios there's a setting to output first to DVI
then, type this in the terminal
sudo nvidia-settings
then enable the secondary monitor in the GUI, and have it write an xorg.con file for you
then replace it (you might need to saave it first to the desktop, and then replace through the terminal with 'sudo mv xorg.conf /etc/X11/xorg.conf')
mine works great!

---

### Post by brecasx on 2007-11-22
I'm thinking about getting a T61 (with NVIDIA Quadro) and a 24" samsung or dell monitor.  

When you guys say that it works do you mean that if I put the laptop on the dock I will have both screens on?  If I put the laptop on the dock will it automatically put the desktop on the external?  Do you have to reboot to get the setup to work?

Cheers!

---

### Post by grmbrand on 2007-11-26
Hey pwhite & syxbit -- thanks for the pointers. I, too am now successfully running my (cloned) external monitor with my laptop shut and docked. I notice that the TwinView cloning does funny things with the Gnome toolbars, but that seems to be a Gnome problem that other users have experienced as well. I am off to the races.

Thanks again!
--Grmbrand

---

### Post by cmdln on 2008-03-03
Im considering getting a T61. I am curious has anyone tried running tri head? There is a vga and dvi port on the dock. Can you span your desktop across three monitors?

---

