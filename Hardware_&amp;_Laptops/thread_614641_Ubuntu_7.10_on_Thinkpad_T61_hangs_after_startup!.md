---
title: "Ubuntu 7.10 on Thinkpad T61 hangs after startup!"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by afroozeh on 2007-11-16
I have a Thinkpad T61 2.2 Ghz, 1 GB RAM and 160 gb hard disk.
I have installed ubuntu 7.10 and everything was great. I used wireless network and upgrade my softwares. installing some new ones.
but when I started my laptop next morning during startup or after log in computer hangs and caps lock light below monitor starts to blik! I saw the logs it says its a kernel panic or something.
I found out it is the wireless problem. when wireless is shutdown everything is ok but when I turn it on the system hangs. wireless feature works fine in vista so I dont think it might be a hardware problem!
I also tries the open suse 10.3 during install it hangs. the same wireless problem.
any suggestion? I mean its kernel problem? or linux driver?

Thanks is anticipation.

---

### Post by syxbit on 2007-11-17
install from the alternate disc
then, upon first boot, choose the second option in the grub (the recovery mode)
then, when you reach a terminal type this
dpkg-reconfigure xserver-xorg
pick vesa video driver, and keep everything else normal
then, reboot, and pick the top option in the grub.
then, when you get into X (a regular OS with video) in the terminal type
sudo apt-get install nvidia-glx-new
then type
sudo nvidia-xconfig
reboot
you should be good to go

---

