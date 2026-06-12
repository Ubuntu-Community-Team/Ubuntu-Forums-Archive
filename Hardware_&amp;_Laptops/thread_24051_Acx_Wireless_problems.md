---
title: "Acx Wireless problems"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by Darth_Nader on 2005-04-05
I have a Netgear Wg311v2, which is a acx111 card. It will associate when I bring down eth0, but after a few seconds it stops transfering data. In the firmware text, in the acx folder, it mentions that this perticular card won't work any signifigant amount of time with the current firmware. I replaced the default firmware with the firmware from the Netgear site. It still does the same thing. How do I make Ubuntu use Ndiswrapper instead of Acx? I installed Ndiswrapper and wlan0 is still configured as acx_version8 device.

---

### Post by ubuntu_newbie_mike on 2005-05-11
I know im late (maybe to late), but this could be useful for any other too ;-)

I use a sitecom wireless card, that has the same chipset (acx111), and i had the same problems with the acx-module, that came out-of-the-box with the installation. So i decided to install ndiswrapper. The installation was successful, but at the bootup acx started before ndiswrapper and so it blocked it and i had the same problems as before. The instructions in the ndiswrapper documentation to modprobe it in /etc/network/interfaces did not work. I tried to deaktivate the hotplug for the network cards with the same result.
Finaly i added ndiswrapper to /etc/modules and now it starts before acx and so all works fine.

Does anybody know how to tell ubuntu not to start acx anyway?

---

