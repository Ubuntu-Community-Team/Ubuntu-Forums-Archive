---
title: "Xserver won't start"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by graphisong on 2007-11-29
Hello. I just recently purchased an HP dv6646us laptop. Tonight I installed UbuntuStudio Gutsy, but I cannot boot into my Xserver. I have a dual boot with Vista Home Premium, which I want to keep (Yikes!) When I get to booting UbuntuStudio, which is necessarily installed from an alternate install dvd, there is a fatal error: "No Screens Found

Jim Adams

:guitar:

---

### Post by graphisong on 2007-11-30
I found the solution. I just did a dpkg-reconfigure xserver-xorg, and chose the "vesa" driver instead of the "nv" driver.

Thanks

Jim Adams

---

### Post by adityakavoor on 2007-11-30
mark the thread as solved to make it easy for other users

---

### Post by PmDematagoda on 2007-11-30
Since the PC has an Nvidia card vesa would not let the Nvidia card run at it's true potential.

Try and use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to see if you can get your Nvidia card working on your PC.

---

