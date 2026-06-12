---
title: "Weird wifi problem"
date: 2009-10-24
forum: Hardware
---

### Post by zenil on 2009-10-24
Hi everyone, I've finally installed Ubuntu 9.04 in my laptop and I really love it. The problem is...the wifi card doesn't works. It is weird because when I booted the cd, y used the try & install feature. There, everything worked, the wifi, the graphics card, etc. But when I installed it, I couldn't find any wireless network like I did when using the Live cd. I am new to Linux and I really like it, please help! Thanks in advance :)

---

### Post by lidex on 2009-10-25
Look at post no.8 in this thread and let me know if it helps:

[http://ubuntuforums.org/showthread.php?t=1289484]("http://ubuntuforums.org/showthread.php?t=1289484")

---

### Post by zenil on 2009-10-25
Nope, still the same :(
I ran "lshw" and I got  
....
*-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:43:61:f5:2e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
....
Hope it helps :S

---

### Post by lidex on 2009-10-25
Try rebooting again.Then look here:
[http://ubuntuforums.org/showthread.php?t=894177]("http://ubuntuforums.org/showthread.php?t=894177")

---

### Post by zenil on 2009-10-25
Nopre, I followed all the instructions, installed the drivers, rebooted and everything, but still the same :(
I dont know, but I think I have the drivers beacuase the wireless card is detected, and in the Live cd I can connect without problems. I dont know why it doesn't works.:(

---

### Post by zenil on 2009-10-26
got the answer! there were conflict withh Bluetooth. Deactivated it and enabled wifi in etc/rc.local
Thank you veery much for your help

---

