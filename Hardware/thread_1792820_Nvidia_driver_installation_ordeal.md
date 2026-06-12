---
title: "Nvidia driver installation ordeal"
date: 2011-06-28
forum: Hardware
---

### Post by rreyes3713 on 2011-06-28
I have a Nvidia GeForce FX Go5200 video card on my laptop.

I went to the Nvidia website to get the appropriate driver for this card and and download the following file:

NVIDIA-Linux-x86-173.14.30-pkg1.run

So I did the following:

sudo sh NVIDIA-Linux-x86-173.14.30-pkg1.run

but end up with the following message:
> 
ERROR: You appear to be running an X server; please exit x before installing. For Further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download pager at [www.nvidia.com]("http://www.nvidia.com")
Well on the Nvidia README page and it doesn't show how to installing in UBUNTU just the other Linux vendors.

Currently I'm using the default driver that Ubuntu suggested (Linux-x86 173.14.22)  but most video clip, the resolution is terrible when I know the resolution was much better on my other laptop installed with Ubuntu with the stock video card.

Help, yes I did a search and many Nvidoa posts came up. Can't sort out which applies to me.

Thanks,

---

### Post by wolfen69 on 2011-06-28
[http://www.linuxforums.org/forum/red-hat-fedora-linux/152347-solved-how-exit-x-server-mode-inst-nvidia-drivers.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/152347-solved-how-exit-x-server-mode-inst-nvidia-drivers.html)

---

### Post by Dlambert on 2011-06-28
sudo /etc/init.d/gdm stop to stop Gnome, but if you already have the ubuntu one installed, remove it. I would recommend just holding shift when grub starts to launch ubuntu in recovery console. Then login, sudo PATH ./N(hit tab to bring full name) and install.

---

