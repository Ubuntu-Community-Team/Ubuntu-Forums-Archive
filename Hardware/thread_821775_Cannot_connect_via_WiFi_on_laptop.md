---
title: "Cannot connect via WiFi on laptop"
date: 2008-06-07
forum: Hardware
---

### Post by Arphahat on 2008-06-07
I just installed Ubuntu on my old Sony Vaio.  I use an old Linksys WPC54Cv3.  I know that the card works because I previously used it on this machine when I had XP installed.

When I try to "Connect to other wireless network" and type in the network name and key, it tries to connect but eventually pops up the "wireless network key required" window again.  I am certain that I am using the correct key.

Do I need to have special drivers for the card?  Are they already installed and not being used?  I am very new to Ubuntu and this is the first laptop that I am trying to run it on.  Any help would be appreciated.

Thanks,
Andy

---

### Post by Wobblybob on 2008-06-07
Hi,

try [system], [Admin..], [Hardware drivers] to see if you need the restricted drivers enabled, if they are listed and need enabling you will need to connect the laptop via a cable to your internet connection to allow it to download and install them. A reboot will then be required and you should check back in hardware drivers again to make sure they are enabled and in use.

---

### Post by Arphahat on 2008-06-07
Thanks for your help.

The "Hardware Drivers" window says "No proprietary drivers are in use on this system."  I assume this means that something else is going on?

---

### Post by Arphahat on 2008-06-07
I decided to try running the "Hardware Testing".  It lists the Linksys as a "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g".  Could this be the problem?

---

### Post by Wobblybob on 2008-06-07
Have a look at this thread, it may help with your problem. [http://ubuntuforums.org/showthread.php?t=190177]("http://ubuntuforums.org/showthread.php?t=190177")

---

### Post by Arphahat on 2008-06-07
Thanks for your help.

What finally fixed the problem, for the record, is that I connected the laptop to the Internet via an Ethernet cable, did an update and then was able to select the hardware option in hardware drivers, the space you originally mentioned.  After a reboot, all was good.

---

