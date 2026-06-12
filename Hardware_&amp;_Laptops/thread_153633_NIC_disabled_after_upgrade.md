---
title: "NIC disabled after upgrade"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by challman on 2006-04-01
I'm not getting much help on the Kubuntu forums, so I decided to post my problem here. I've recently installed Kubuntu 5.10.. Everything works fine (apps, desktop, networking, internet, etc.) until after I upgrade (sudo apt-get update; sudo apt-get upgrade) and reboot. After the reboot, my NIC is disabled. /etc/network/interfaces contains:

mapping hotplug
   script grep
   map eth0

#the primary network interface
iface eth0 inet dhcp


I've tried sudo /etc/init.d/networking restart but it fails. When I boot into WinXP, the NIC works fine. I don't know what else to do. Here is my system:

Intel P4 3.0Ghz w/ HT
Nvidia GeForce 4 Ti 4800SE 128MB
1GB DRAM (two 512MB DIMMs) dual channel PC3200
Realtek 8100BL 10/100Mb Ethernet
hda0 30GB WinXP SP2
hda1 30GB WinXP SP2
hdb0 2GB NTFS SWAP
hdb1 200MB ReiserFS /boot
hdb2 9.5GB ReiserFS /
hdb3 1GB SWAP
Liteon 8x DVD+-RW
Floppy


chris@Kubuntu:/etc$ifconfig -a

eth0 Link encap:Ethernet   Hwaddr 00:40:CA:6C:71:FA
         BROADCAST MULTICAST MTUI:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frames:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collision:0 txqueuelen:1000
         RX bytes:0 (0.0b) TX bytes:0 (0.0b)
         Interrupt:22 Base address:0xa000

chris@Kubuntu:/etc$sudo ifdown eth0
/etc/network/interfaces:20: too few parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"

chris@Kubuntu:/etc$sudo ifup eth0
/etc/network/interfaces:20: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"

chris@Kubuntu:/etc$ifconfig

chris@Kubuntu:/etc$ls -al interfaces
-rw-r--r--   1 root root 484 2006-03-31 10:55 interfaces
chris@Kubuntu:/etc$

---

### Post by jshein on 2006-04-02
This is an issue I have now had on over a dozen machines.

It seems that in some cases the update of dhcp3 has failed. Simply by reinstalling the offending packages from the local apt cache I have been able to fix the probelm.

Use the following command to reinstall the packages.
**#sudo dpkg -i /var/cache/apt/archives/dhcp3-c***

After this simply restart the network.
**#sudo /etc/init.d/networking restart**

You should now be up and running!

---

### Post by challman on 2006-04-02
That did the trick!!!   Thanks!

---

