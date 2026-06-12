---
title: "D-Link network card lost"
date: 2008-07-31
forum: Hardware
---

### Post by MelkorBauglir on 2008-07-31
Hello All, 

I have troubles with d-link dge-560T. The history is that: 

There is a computer with 3 network adapters (beowulf-type cluster head node)

 - onboard nvidia nforce (nVidia Corporation MCP67 Ethernet)
 - via vt6105 ( VIA Technologies, Inc. VT6105 [Rhine-III])
 - d-link dge560  (D-Link System Inc DGE-560T PCI Express Gigabit Ethernet Adapter)

All cards have been successfully found by the system and configured by udevd in /etc/udev/rules.d/70-persistent-net.rules. This file contains records for all 3 cards and interfaces. 

After the initial install all adapters work fine without any issues. However, by some unknown reason D-Link card automatically disables after the reboot and I was failed to enable it. 

The system responses are the following: 
-------------------------------
% sudo ifconfig eth2
eth2: error fetching interface information: No such device

% sudo ifup eth2
eth2: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth2: ERROR while getting interface flags: No such device
Failed to bring up eth2.
------------------------------- 

lspci command said that all cards are present. 
-------------------------------
% lspci
...
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
...
01:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
01:07.0 Ethernet controller: D-Link System Inc DGE-560T PCI Express Gigabit Ethernet Adapter (rev 11)
-------------------------------

It looks like D-Link driver does not load. 

"% sudo lshw -C network" command says D-Link is present but unclaimed. 

I am on Ubuntu 8.04 Hardy. 

Any thoughts of how it can be fixed? 

Thanks in advance.

---

### Post by MelkorBauglir on 2008-07-31
Any thoughts or suggestions?

---

