---
title: "Solution To Ati Crashing X server"
date: 2009-11-23
forum: Hardware
---

### Post by .:DSHacker:. on 2009-11-23
Hi, I've been battling to be able to get to work my 3100HD ati card with fglrx but, it always made the xserver crash, and as I have seen I'm not the only one...

Today, installing de 9.11 driver from ati (ati.amd.com/drivers/) didn't work either =(.

Note: I downloaded the drivers from ati.com....

So in the recovery shell as i was deleting xorg.conf to re-establish open source drivers, I made an 

```
sudo aptitude search fglrx
p   fglrx-amdcccle                  - Catalyst Control Center for the ATI graphi
p   fglrx-kernel-source             - Kernel module source for the ATI graphics 
i   fglrx-modaliases                - Identifiers supported by the ATI graphics 
p   xorg-driver-fglrx               - Video driver for the ATI graphics accelera
p   xorg-driver-fglrx-dev           - Video driver for the ATI graphics accelera

```To un-install fglrx since I didn't found ./fglrx-uninstall.sh and I purged fglrx-modaliases...

I rebooted and my desktop effects worked! and i had an 6000 FPS in glxgears!

So the steps are:


[LIST=1]
[*]Install driver 9.11 from ati.amd.com
[*]Purge package fglrx-modaliases
[*]Reboot and Enjoy!
[/LIST]


I don't know if it will work for you, but it's the only way i had made desktop effects work!!!

Please Try It and comment

PS: Sorry If I have a bad english....I'm a spanish speaker

---

