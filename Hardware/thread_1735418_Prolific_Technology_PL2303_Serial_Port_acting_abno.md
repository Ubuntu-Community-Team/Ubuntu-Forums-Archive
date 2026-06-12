---
title: "Prolific Technology PL2303 Serial Port acting abnormal on Dell T1500 Ubuntu 11.04"
date: 2011-04-21
forum: Hardware
---

### Post by ethandu on 2011-04-21
I am using Prolific Technology PL2303 Serial Port on Dell T1500, with Ubuntu 11.04

# lsusb
Bus 001 Device 022: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

The device ttyUSB0 can show up on PC, and minicom/gtkterm can be started on this device. However, during the usage, there will be data lost. I verified the cable with minicom/gtkterm/cu work well on another Dell 380, with Ubuntu 11.04.

Anyone seen similar thing before?

Any suggestions?

Thanks,
-Ethan

---

### Post by gerkin on 2011-07-23
Hi

I have the same USB/serial converter and it stopped working in Ubuntu 10.10, but worked fine in all previous versions up to 10.04-2 LTS

This is a show stopper for me and has stopped me upgrading and I have since found the same problem with Xubuntu 11.04

The is are at least one  reported bug about this:

[https://bugs.launchpad.net/network-manager/+bug/700316](https://bugs.launchpad.net/network-manager/+bug/700316)

The only suggestion I have is to run either 10.04-2 LTS of try another distro

I would be keen to hear if you find a solution as I haven't had any luck yet but will post a solution here if I find it

cheers........gerkin

---

### Post by ethandu on 2011-07-26
I switched to another same cable, and it works for me now.

---

### Post by mhdanas.n on 2011-08-13
> **ethandu said:**
> I switched to another same cable, and it works for me now.

so u mean u just have another PL2303 cable and it work ?!, cuz i have same problem and the cable work fine on windows, and not find solution till now with this :(

---

