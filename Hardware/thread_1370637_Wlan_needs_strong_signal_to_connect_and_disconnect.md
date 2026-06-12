---
title: "Wlan needs strong signal to connect and disconnects occasionally"
date: 2010-01-02
forum: Hardware
---

### Post by sharq1 on 2010-01-02
Hi, on Jaunty wifi was fine, on Karmic it works strange. I can see a lot of access points, but i can connect to ones that's signal strenght is above approximately 60%. When i finally connect to AP then after some (longer) time i can't open any new site, but internet radio still plays if it was connected earlier. So it looks like i can't start any new connections.
Can anyone help me with this one?

---

### Post by kluffinator on 2010-01-02
I've had similar problems with Karmic on a number of laptops, mostly Gateways with Atheros wireless cards.

For me, the wireless would disconnect often and rarely reconnect.

The workaround:
1. Open a terminal
2. sudo apt-get update
3. sudo apt-get install linux-backports-modules-karmic
4. Restart your computer.

If this doesn't work, type lshw into a terminal and post it here. 

Good luck!

---

### Post by sharq1 on 2010-01-02
Thanks for reply, kluffinator.
I tried this one before, it didn't help. Actually then i couldn't even connect to strongest AP in area.

This is part of lshw output
>            *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:43:08:b5:5e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f8000000-f800ffff


---

### Post by sharq1 on 2010-01-04
I installed madwifi from this tutorial and it works for now:
> [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

