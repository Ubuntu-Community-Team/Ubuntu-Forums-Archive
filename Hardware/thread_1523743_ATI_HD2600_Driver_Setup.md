---
title: "ATI HD2600 Driver Setup"
date: 2010-07-04
forum: Hardware
---

### Post by Grovesy on 2010-07-04
Hello,
I have the above graphics card model and wish to install the latest drivers from ATI. I did manage to install them succesfully but each time I install them, Ubuntu 10.04 crashes after approx 30 seconds of use - no matter what applications I try and use. I've now uninstalled them until I can get more advice.

In the instructions [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat106-inst.pdf"), the Minimum Sytem Requirements AND the System Requirements state the following ...

> [SIZE=4]Minimum System Requirements[/SIZE]
Before attempting to install the ATI Catalyst™ Proprietary Linux driver, the following
software must be installed:
&#1048698; XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4 or 7.5
&#1048698; Linux kernel 2.6 or above
&#1048698; glibc version 2.2 or 2.3
&#1048698; POSIX Shared Memory (/dev/shm) support is required for 3D applications
Note: If a Linux 2.6.11 or newer kernel was built with
CONFIG_AGP enabled, the kernel AGP frontend is required to load
the fglrx kernel module. To identify whether your kernel was built
with CONFIG_AGP enabled, look for CONFIG_AGP=y in the
kernel config file, or if the 'agpgart' module is loaded.

[SIZE=4]System Recommendations[/SIZE]
For best performance and ease of use, ATI recommends the following:
&#1048698; Kernel module build environment
o Kernel source code include either the Kernel Source or Kernel Headers packages
&#1048698; The RPM utility should be installed and configured correctly on your system, if you
intend to install via RPM packages
The following packages must be installed in order for the ATI Catalyst™ Linux driver to
install and work properly:
&#1048698; XFree86-Mesa-libGL
&#1048698; libstdc++
&#1048698; libgcc
&#1048698; XFree86-libs
&#1048698; fontconfig
&#1048698; freetype
&#1048698; zlib
&#1048698; gccI've managed to set the POSIX setting but am not sure about how to go about setting the CONFIG_AGP setting properly. I think it's set to CONFIG_AGP=m (assuming I'm looking at the right file - config-2.6.32-23-generic). Any one?

Also, How do I go about checking versions of XOrg, glibc and the linux kernel installed.

Finally how do i check if the packages under System requirements are installed?

Hope someone can help as I'd really like to get my graphics card working with a proper driver. Hopefully I'll then be able to watch iPlayer and other videos without the picture being jerky.

---

### Post by mihaill on 2010-12-25
hello! 
For starters I have the same card... I've managed to install the drivers and the catalyst but when I open a window it flickers when I move it... the same problem appears when I scroll down a web page... 
video playing seems ok ...
when I don't have this drivers I can not even manage to change the screen resolution!
Also I can not use the visual 3d effects of ubuntu 10.10 ...
what is a full functioning Aticonfig anyway (after the install a message appears that I have a basic config for ati drivers)...?

---

