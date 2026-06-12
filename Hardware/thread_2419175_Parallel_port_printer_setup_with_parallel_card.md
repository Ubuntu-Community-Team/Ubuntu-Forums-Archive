---
title: "Parallel port printer setup with parallel card"
date: 2019-05-17
forum: Hardware
---

### Post by mvJLokq3tT on 2019-05-17
I'm running Kubuntu 18.04 LTS and am trying to get a HP Laserjet 1100  parallel port printer to work with a parallel port card. The card  reports itself with the following when running *sudo lspci  -v*:

> 09:01.0 Parallel controller: SUNIX Co., Ltd. Multiport serial controller (prog-if 03 [IEEE1284])
Subsystem: SUNIX Co., Ltd. Multiport serial controller
Flags: medium devsel, IRQ 5
I/O ports at e800 [size=8]
I/O ports at e480 [size=8]
I/O ports at e400 [size=16]
Capabilities: [40] Power Management version 3

Following the instructions I found here, [https://ubuntuforums.org/showthread.php?t=1233589](https://ubuntuforums.org/showthread.php?t=1233589) I did the following:
[I]
sudo modprobe parport_pc io=0xe800
sudo modprobe lp
sudo /etc/init.d/cups restart[/I]

When I then run *hp-setup* the printer is found and can  print. *ls -l /dev/parport** shows the following:

> crw-rw-r-- 1 root lp 99, 0 Mai 17 15:19 /dev/parport0

To make all this permanent, I created the file parport_pc,

[I]sudo nano /etc/modprobe.d/parport_pc
options parport_pc io=0xe800[/I]

and put it into modules:

[I]sudo nano /etc/modules

parport_pc
lp[/I]

However, after a reboot all the information is lost. Any jobs send to  the printer end up being indefinitely on hold in the printer spool and *ls -l /dev/parport** comes up empty. 

I'd appreciate any help here, because I'm seriously stumped.

---

