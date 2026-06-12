---
title: "Fglrx drivers in edgy"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by neoncode on 2006-10-17
Hello, I assume this is the correct forum. I have an ATi Radeon 9600 and I'm running Kubuntu edgy.I carn't seem to install and run the fglrx driver. I have folowed the guide on the ubuntu wiki and several of the guides here. But it does not work, fglrxinfo prints:

> $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


According to the wiki this means that it's not setup properly, I've followed a lot of guides so I'm not sure where I went wrong. I know it's possible because I had the fglrx drivers in Dapper and Hoary. Please, any help is much appreciated.

---

### Post by knota on 2006-10-19
Hi,read folloving link for fglrx and edgy.
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually)

If not work try to edit /etc/modules it works fine for me in edgy.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
#ATI Radeon 9600 Kubuntu edgy
lp
fglrx
#

---

### Post by zachtib on 2006-10-19
> **knota said:**
> Hi,read folloving link for fglrx and edgy.
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually)

If not work try to edit /etc/modules it works fine for me in edgy.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
#ATI Radeon 9600 Kubuntu edgy
lp
fglrx
#

you might try the radeon driver as well.

radeon has full hardware accel up to the 9200, and they have reverse engineered everything up to the X800.  its just a matter of setting up your xorg.conf properly.

---

