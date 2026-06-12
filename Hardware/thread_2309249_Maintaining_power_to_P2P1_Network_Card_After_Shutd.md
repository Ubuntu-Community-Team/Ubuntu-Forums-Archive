---
title: "Maintaining power to P2P1 Network Card After Shutdown"
date: 2016-01-08
forum: Hardware
---

### Post by robo731 on 2016-01-08
I am trying too implement wake on lan on a Dell Inspiron 15r (5521) laptop. I believe that the laptop is indeed receiving the packets (at least when it is on), but I think that the network card is not maintaining power after the system has been shutdown by running: ```
sudo shutdown -h now
``` I am able to wake the laptop up from sleep (suspend mode). Is there a way to ensure that the NIC will have power once the system is shutdown?

---

### Post by weatherman2 on 2016-01-08
Try answer #6 here:

[http://www.linuxquestions.org/questions/linux-general-1/wake-on-lan-doesn't-work-after-linux-shutdown-841960/](http://www.linuxquestions.org/questions/linux-general-1/wake-on-lan-doesn't-work-after-linux-shutdown-841960/)

which suggests running this command (assuming your network card is eth0):

```
ethtool -s eth0 wol g
```

"Then tell the machine to shutdown and then hit it with a WOL packet and see if it wakes up. If that solves your problem then put that ethtool command somewhere it will get run automatically such as /etc/init.d/halt.local" - not sure if halt.local is the right place for Ubuntu, however...

---

### Post by robo731 on 2016-01-09
Yeah, I've already done that. Fortunately for me, my machine has that set by default. I think the problem is that the card isn't being powered once it's off.

---

### Post by tgalati4 on 2016-01-09
Install acpitool and post:

```
sudo apt-get install acpitool
acpitool -w
```

Use the -W switch to keep power to the part of the bus that your network card is attached to.

Laptops are tricky, since they are not designed for this Use Case.  Typically WoL only works when the computer is put to sleep, not powered off.  Some Dell PowerEdge servers will do either Boot-on-Lan or Wake-on-Lan if the network card is enabled (using the "g" switch), BIOS WoL is turned on, and you don't loose power.  Sometimes the network card needs to set to "g" mode during each boot since some cards don't keep the setting in flash RAM.  To accomplish this, put the ethtool commands in /etc/rc.local so the network card gets set to "g" mode during each boot.

---

### Post by robo731 on 2016-01-09
Here's the output: ```
   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. P0P1         S0    *disabled
  2. EHC1         S0    *enabled   pci:0000:00:1d.0
  3. XHC          S0    *enabled   pci:0000:00:14.0
  4. RP01         S3    *disabled  pci:0000:00:1c.0
  5. RP02         S0    *disabled  pci:0000:00:1c.1
  6. PEG0         S4    *disabled
  7. PEGP         S4    *disabled
  8. PEG1         S4    *disabled
  9. PEG2         S4    *disabled
  10. PEG3        S4    *disabled
  11. LID0        S3    *enabled   platform:PNP0C0D:0 
```

The ethernet card is p2p1 though, and I don't see it listed there. The laptop does seem to retain the "g" setting as it is set to "g" any time I check, even after reboots. Should I still put the ethtool commands in /etc/rc.local?

I called Dell to find out if this was possible. It seems there's no way  to set the laptop to keep power to the network card after an S5  shutdown. Such functionality is only available in their enterprise  systems. The fact that you can wake from sleep mode is the best work  around I can find.

---

