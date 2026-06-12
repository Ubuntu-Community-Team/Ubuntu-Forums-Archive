---
title: "Geforce gt 130M on UbuntuStudio Karmic"
date: 2010-03-30
forum: Hardware
---

### Post by Lord M on 2010-03-30
Hello everyone,
I am going crazy trying to get a full installation of my Geforce on the laptop I use.

it's a 

Geforce gt 130M 1Gb

The PC is a laptop witn Centrino 64 bit dual processor, 4Gb ram.

Display 15" 16:9 ratio 1366x768 refresh rate 60Hz

The distro I am using is an UbuntuStudio Karmic 64bit.

Compiz is running as Window Manager, but it can be changed is it is the problem (I changed the default metacity with it).

I found around a lot of people (even on this forum) that had troubles with nvidia driver but none has my problem.

First I run the hardware device detection and this advice me on installing a certified not opensource driver from nvidia version 185 and the system cannot start at all, I just see a white dash line on the top of the monitor.

I tried to install the package version 195 from nvidia.com with the 

sh ./

from a terminal session. It worked according to the installer but at restart I see a flashing monitor from black to terminal login (even if I have set the graphical login).

Also tried from the repository everyone uses adding to the list

[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

I checked the configuration and should be fine but it gives the same error at restart. Plus on the command 

nvidia-xconfig

it gives an error message that the command line was limited to the version 185 (plus other two but not 195 I installed) of the package and can't be found.

Tried from Synaptic with the repository, same results.

Also tried out envy application, it can't work with the latest 195 drivers.

Actually they install the application under system administration, I can run it, write the config, but at restart I can't even login... and I can't find a way to take back the old configuration (there was not an old config file to reload) so I just reinstall the distro right away keeping the /home and other disks unchanged. Just formatting the OS disk.

Any idea of settings or something that can cause conflicts?

---

