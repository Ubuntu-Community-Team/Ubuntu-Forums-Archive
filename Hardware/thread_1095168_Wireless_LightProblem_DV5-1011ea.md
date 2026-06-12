---
title: "Wireless Light/Problem DV5-1011ea"
date: 2009-03-13
forum: Hardware
---

### Post by acidPython on 2009-03-13
Hi, i'm currently using a HP DV5 1000 series laptop. I used to run ubuntu/vista dual booted and there was one bizarre problem;

The wireless on my laptop could be turned off/on via a feature on the touch panel which i could only get working in vista. Now that i'm running linux as my only OS I can't seem to turn the light back on to enable my wireless.

Is there anything I can do to enable the wireless?

Tried;
changing keyboard model in xorg.conf (its set right apparently)
looking in BIOS for a feature to turn it on.

---

### Post by pytheas22 on 2009-03-13
Please try toggling the switch on and off a few times, then post the output of these commands:
```

sudo iwlist scan
dmesg | grep -i -e radio -e wlan -e unknown
lshw -C Network
```

Also, note that in some cases the light may not come on, but the wireless is still working.  The only way to know for sure whether the wireless is working is to run the command 'sudo iwlist scan'; if the radio is enabled, it will show you a list of networks.

---

