---
title: "PHY Transmission error?? answer in an easy way."
date: 2008-10-01
forum: Hardware
---

### Post by saggitheman on 2008-10-01
I have a Dell Latitude D600 With Ubuntu 8.04 Hardy Heron... But when i start it up i get a black screen that says PHY Transmission Error! WHY!? I's it something wrong? Everything seems to work fine, i have no problems with enything... So what should i do?

---

### Post by ZedsDeadBaby on 2008-10-15
I would like to bump this.  Same situation here.  D600, Hardy 8.04, same error:

[ 82.275759] b43-PHY0 error: PHY Transmission Error
[220.522796] b43-PHY0 error: MAC Suspend Failed

These ONLY occur when booting on battery (without AC power charger attached).  But they occur nearly everytime.  Also, when the system does boot fully, the system will freeze within 20 min, to the point nothing works and you need to press the power button for 5 seconds to kill the system.

BUT... on AC the system is stable and running great.

Specs: Dell Latitude D600, current BIOS, 2gb ram, 250gb HDD.  System is only hosting this OS, so no interference for grub with Windows or something.

Please help & thanks to all!!!

---

### Post by gargouille on 2008-11-25
I had a similar issue with Intrepid Ibex:

> **gargouille said:**
> HARDWARE:
Dell Latitude D600
Broadcom BCM4309 (bcm43xx)


PROBLEM:
Wireless connection disconnects.  When shutting down, or rebooting, the following error appears and keeps repeating:  b43-phy0 ERROR: PHY transmission error

kern.log entry:
Nov 25 18:25:57 coruscant kernel: [   92.216246] wlan0: no IPv6 routers present
Nov 25 18:26:02 coruscant kernel: [   96.820027] __ratelimit: 386 callbacks suppressed
Nov 25 18:26:02 coruscant kernel: [   96.820027] b43-phy0 ERROR: PHY transmission error


FIX:
found in Ubuntu help:

3.3.6.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---

### Post by flanagan on 2009-03-19
An older thread, I know, but I just want to thank gargouille for that answer regarding ipv6. I just came across an old, cheap Latitude D505 with the same b43 chip and it has been a real dog to get working. I think the last hurdle has been the disabling of ipv6. It used to work for five minutes, off for five minutes, on again, off again, etc.

Now it's running smoothly ... :D

---

