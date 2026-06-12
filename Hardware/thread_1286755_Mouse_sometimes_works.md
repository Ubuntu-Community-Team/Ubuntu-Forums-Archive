---
title: "Mouse sometimes works"
date: 2009-10-09
forum: Hardware
---

### Post by oz238 on 2009-10-09
I have Ubuntu 9.04. Every time I start the computer I have to restart it several times to cause mouse working. The mouse is ok - it works under Vista. I also tried other mouse and there is the same problem. 

It is no problem to cause mouse working by typing after Ubuntu loaded:
> 
rmmod psmouse
modprobe psmouse
However, I cannot use remote controler because lirc is not working with manual added psmouse module. The above rmmod shows that psmouse is loaded even if mouse doesn't work.

I tried to add 'psmouse' to /etc/modules and file with options to /etc/modprobe.d/. But it doesn't work.
I tried to change configuration within xorg.conf. And it also doesn't work.
I tried to add 'sudo modprobe psmouse' to rc.local - it doesn't work.
I cannot understand why mouse works in random way.

These are dmesg infos when mouse works:
> 
[   14.967479] psmouse serio1: ID: 00 00 3c<6>Linux video capture interface: v2.00
[   14.924639] psmouse serio1: ID: 00 00 3c<6>tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
And these are dmesg info when mouse doesn't work.
> 
[   14.062960] psmouse serio1: ID: 00 00 3c<6>iTCO_vendor_support: vendor-support=0
[   13.998756] psmouse serio1: ID: 00 00 3c<6>Linux agpgart interface v0.103
[   14.578746] psmouse serio1: ID: 00 00 3c<6>nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16



I found the solution. The reason for this was not proper configuration of lirc. Simply lirc was connected to mouse and nor remote doesn't work neither mouse. Specify proper name for lirc device:
not /dev/input/event5, but: 
/dev/input/by-path/device

---

