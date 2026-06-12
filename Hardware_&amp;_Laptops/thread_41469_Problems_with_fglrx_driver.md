---
title: "Problems with fglrx driver"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by Hanj on 2005-06-13
I just installed Kubuntu 5.04 and I have a Radeon 9200 card. The performace was crappy with the radeon driver, so I though I'd install the proprietary drivers from Ati. Now, I know there are tons of guides to do this in these forums, but I've tried everything I found and nothing works. 

First of all, I tried downloading the installer from [www.ati.com](www.ati.com), and created xorg.conf with fglrxconfig, but then 3D acceleration got turned off and lsmod says nothing about fglrx. So then I tried the official package with synaptic, but nothing seemed to happen.

I then found the following instructions and followed them:

1. download official driver .rpm from ATI
2. remove fglrx packages using Synaptic
3. shut down Gnome (terminal: sudo /etc/init.d/gdm stop)
4. cd to download-location
5. sudo alien fglrx_ ... .rpm
6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. sudo dpkg --force-overwrite -i fglrx- ... .deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. sudo modprobe fglrx
13. sudo fglrxconfig

This works fine until step 11 where I get this error:
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko): Operation not permitted failed.

It seems some people could ignore this error and still get it to work, but it doesn't work for me.

fglrxinfo says:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

glxinfo|grep rendering says:
direct rendering: No

Oh, and "modprobe fglrx" also produces the "operation not permitted" error.

[EDIT]I just tried removing everything and reinstalled the xorg-driver-fglrx package. Now modprobing no longer produces an error and "lsmod | grep gl" gives me this:
fglrx                 235004  0
However, I still don't get 3D acceleration. fglrxinfo says the same thing as before and glxgears runs really slow. I changed the "Driver" entry in xorg.conf to "fglrx" and rebooted, but no luck. How do I turn on hardware acceleration? [/EDIT]

---

### Post by Hanj on 2005-06-14
Never mind, I fixed it. I just kept trying the same things over and over and for some reason it just started working. Weird.

---

