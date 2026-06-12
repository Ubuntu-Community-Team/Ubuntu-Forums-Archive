---
title: "Problems with Touchpad Mouse"
date: 2008-09-11
forum: Hardware
---

### Post by crackerdog2 on 2008-09-11
Last week I was running Ubuntu 8.04 on an HP Pavilion dv8000 with ATI Radeon Xpress 200M. After installation, I had various problems with the display settings and I could not get the desktop icon's smaller  and the logout screen went off to the  screen every time I tried to log out.

So I decided to uninstall KDE and go back to Gnome. But me being relatively  new to Linux, didn't realize that there was a apt-get remove kde-desktop, or whatever the proper command is. So I searched for all packages in Synaptic Package Manager that had KDE in it and I removed them all. Boy was that a mistake. :(

Fortunately I got my computer back up and running, for the most part. Now my touchpad is giving me troubles and it even seems like, as I am typing this out, my key board is not typing correctly either.

Going to the terminal and running the dmesg command it is showing the following, repeatedly:

[  508.344267] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=192.168.1.255 LEN=223 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=203
[  508.344548] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC= SRC=10.2.25.77 DST=10.2.255.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=200
[  524.845886] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=192.168.1.255 LEN=223 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=203
[  532.529006] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  532.530384] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  532.531762] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  532.533477] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  532.543724] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.

Any ideas as to what I should do or try?

---

