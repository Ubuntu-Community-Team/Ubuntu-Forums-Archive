---
title: "When testing UPS, Ubuntu freezes except for one network service"
date: 2016-09-21
forum: Hardware
---

### Post by tannedin on 2016-09-21
The basics of the scenario are an Ubuntu Desktop and a Cyberpower 1000AVR UPS.
When I run Cyperpower's powerstart utility to test, I unplug the UPS from the wall, or a momentary power drop at my location: the machine in question appears to freeze.  I cannot remote, via TeamViewer, into the box nor can I SSH into the box.  Also, VirtualMachines configured also fail remoting & SSH access.  However, a video streaming service called Plex continues runs fine.  All system logging appears to stop when a change in power state occurs, or I haven't found what I should be looking for.

Upon pressing the reset button on the case, turning off/on the machine via power button, or turning off/on the UPS, the machine boots normally with no errors or warnings.

Details on Desktop:
LUbuntu 16.04.1 LTS 64 bit.  Kernel: Linux 4.4.0-38-generic (x86_64)
G1 Sniper 3 motherboard (Wake on Power & Wake on LAN configured)
2x ATI Radeon 5700 using crossfire
Power Settings: (settings -> Power Manager: "XFCE Power Manager" -> "System Tab") "On Battery" & "Plugged In" set to suspend (no other option) & "when inactive for" set to never.

Details on UPS:
Cyberpower 1000AVR connected to desktop via USB.
sudo pwrstat -status returns all correct data.
Tested UPS with a laptop that had the battery removed and it works as advertised. 

Also, had this problem under Ubuntu 16.04.1, 14.04, and 12.04 (default and flavors). Finally admitting that my google-foo isn't strong enough on this one. There are a multitude of automated services I would like to do, but it is a little difficult to maintain a home server that cannot reliably stay online.  I am looking for solutions and/or guidance on tracking down the problem.

---

