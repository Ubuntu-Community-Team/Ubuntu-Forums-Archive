---
title: "Aspire V5-573G Install (might be useful for new folks with this laptop). 14.04 dualb"
date: 2014-10-01
forum: Hardware
---

### Post by Luca.es on 2014-10-01
Hi!

In case anyone has a Aspire V5-573G laptop with the Core i5-4200U and the NVIDIA GT750M GPU here is how I installed Ubuntu alongside Windows 8.1 and some additional feature I find essential.

(Before you install there is no need to disable UEFI/SecureBoot (Windows 8 won't boot in Legacy mode anyway)

1. Shrink Volume to desirable Size in Windows (so that you have free unallocated space). I chose 75GB orso.
2. Put ubuntu on USB Drive, Boot Installer from USB (F12) during startup 
3. Ubuntu installer won't be able to connect to WiFi for some reason but we don't need it. 
4. When asked about where to install choose "something else" (for some reasons Windows 8.1 is not detected so there is no install alongside option)
5. Make a SWAP of 4GB and a / EXT4 with the remaining space and install. (or your choice of how you manage the free space, just leave the existing partitions alone)
6. When the system reboots it will boot straight back into Windows, reboot and press F2 to get into BIOS.
7. Set bootorder to Ubuntu first in BIOS. 

Upon reboot grub will give you the choice to boot ubuntu or the windows boot manager that will boot Windows. So you have dual boot! Yay.

When in Ubuntu enable the NVIDIA drivers and I suggest you install something called  "prime-indicator" like this:

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install prime-indicator
sudo apt-get install mesa-utils

this will add an indicator to the top bar so you can easily switch between Intel/NVIDIA (you can do this in the nvidia panel too but it is more of a hassle)

I think should ship with something like this by default.

---

### Post by Vladlenin5000 on 2014-10-01
(...)
3. When the WiFi device isn't natively supported it won't work in the live session / install. After installed you can start the troubleshooting.
4. In that scenario you should always choose something else, irrespective of the other OS being detected. It's an UEFI installation after all. The OS not being detect has probably to do with it being hibernated at the time. That's the default - fast boot - for Windows 8.x. You need to turn that off before booting the Ubuntu installation media if you need it to be detected. You can always install the way you did.

How does it work with the hybrid graphics?

---

### Post by Luca.es on 2014-10-01
The wifi worked once the OS was installed. 

I tried disabling fastboot in w8.1 but it made no difference. 

> How does it work with the hybrid graphics? 

The switching itself makes you relogin, but thats about all. 

Gaming performance on the NVIDIA is not as good as on Windows lower fps and stuttering. But only tested with CSGO, still need to test more. Could be a driver thing. 

I remember several years ago linux used compiz stuff that always caused problems but I dont know if that is still the case?

---

### Post by Luca.es on 2014-10-01
Ah one more thing I noticed is that it doesn't auto-dim the display while on battery. Maybe it gets confused with the blacklit keyboard? Manually setting brightness works but automatic would be nice.

---

### Post by Vladlenin5000 on 2014-10-01
It could still be a compiz thing, indeed.
Although I love and use standard Ubuntu's Unity in each and every PC or similar and I hate the LXDE, that's - Lubuntu - what I would use to compare gaming performance.

---

