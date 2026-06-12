---
title: "nvidia-current activated, in use but nvida x driver not running"
date: 2011-02-11
forum: Hardware
---

### Post by exentric on 2011-02-11
hi,
I've install nvidia-current through apt-get and it all went fine. After rebooting I'm back to my desktop tried enabling effects but I can't. Checking under 'Additional Drivers', version current is activated and currently in use. Checking Nvidia X Server Settings it says 
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

and so I did nvidia-xconfig. Though all I got after rebooting is the terminal. Removed the xorg.conf file, reboot and I am safely back in my dekstop.

Been battling this for quite a few days searching all over the net but really can't find any solutions yet.

Any tips?

My system:
uBuntu 10.10 (fresh install)
nVidia 7900GS

---

