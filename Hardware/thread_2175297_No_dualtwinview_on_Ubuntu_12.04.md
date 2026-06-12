---
title: "No dual/twinview on Ubuntu 12.04"
date: 2013-09-18
forum: Hardware
---

### Post by soenke3 on 2013-09-18
Hello everyone,

starting with my first post I face a problem I was not able to solve yet with more than a day of forum/wiki-searching.
Now I hope to receive some Support from you.

In our Office we run a 32-bit Server Version of ubuntu 12.04. The Server manages incoming mails and faxes and Displays them on a Screen. Thereto xserver and openbox with lightdm-gtk was installed on the machine and a TFT-Monitor is connected to the Servers onboard VGA port. This Installation works fine.

Now we would like to install a second Screen (with the same Desktop - a total clone). For that we want to use an already existing NVIDIA Geforce 7300 LE with two DVI ports to connect both Screens. (The Card is definetly able to interact with the rest of the Hardware.)

The nvidia Driver 304.88 was installed with 
```
apt-get install nvidia-current
``` and seems to work fine but unfortunately the Screens (each connected to the DVI port) stay black (with saying "no Signal")

Now I would like to give you some Information in advance:

Executing ```
grep nvidia_drv.so /var/log/Xorg.0.log
``` Xorg.0.log says:
[    45.953] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    47.591] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    48.288] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so

Executing ```
dpkg --status nvidia-current-updates | grep Version 
``` it says: "Version: 304.88-0ubuntu0.0.3"

Executing ```
lspci -nnk | grep -A 2 -i vga
``` says: "01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G72 [GeForce 7300 LE] [10de:01d1] (rev a1)
        Subsystem: LeadTek Research Inc. WinFast PX7300LE-TD128 [107d:5efa]
        Kernel driver in use: nvidia" --> Does "VGA" may lead to the Problem because we use DVI ports?

Executing ```
lshw -c video
``` it says:
 "*-display
       description: VGA compatible controller
       product: G72 [GeForce 7300 LE]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d1000000-d1ffffff memory:c0000000-cfffffff memory:d0000000-d0ffffff"


What else?
There is no xorg.conf in /etc/X11, config files are located /usr/share/X11/xorg.conf.d
I already tried to generate a xorg.conf (done as root) via ```
Xorg -configure
``` but the process stops with "Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log".

Because there was a file xorg.conf.new generated and stored in /root I moved that file once to /etc/X11 and /usr/share/X11/xorg.conf.d ... unfortunately with no effects.

Enclose I attache two xorg.0.log files and the faulty(?) generated xorg.conf.new
[ATTACH]246335[/ATTACH]

Looking into "Xorg logfile before reconfigure xorg" it seems in section [49.857] that only one Screen was detected "FUS P17-2 (DFP-1)" the other Monitor (same type) seems not to be detected on DFP-0 ... but why?


Do due both black Screens I have only Access over ssh (putty/winscp) but if neccessary I will post further logs upon request.


I already appreciate your answers and Solutions yet.
Bye for now
Soenke

---

