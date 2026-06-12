---
title: "How to determine if a network interface is toast or just misconfigured"
date: 2015-04-25
forum: Hardware
---

### Post by Evan_Roberts on 2015-04-25
I am a novice at linux admin tasks.  I have a system running ubuntu 10.04. It is controlling a CNC milling machine so upgrading to the latest OS isn't going to be easy.

It has a Gigabyte GA-P41T-D3P mother board with built in Networking.

After working quite a while to configure the system, and failing, I fell back to checking the basics: *are the little lights flashing*? 
Nope. The two LED's adjacent to the network plug are dark.  So I thought maybe I have a bad network cable. I unplugged the network cable from the Gigabyte mother board and into my old Windows XP laptop.  The little LED's on my old laptop lit up quickly. The lights on the router were also lit and flashing. 

I checked the BIOS settings for integrated peripherals and the LAN H/W was enabled. 
 
I've read in other posts that sometimes the network cards become and stay confused until all power is removed. I tried this. Still no connection.

Could I have misconfigured something so badly it would prevent networking from being enabled? 

Here is my network config as of now:
```
smithy@smithy-cnc:~$ **sudo lshw -class network**
[sudo] password for smithy: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:e1:f3:28
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.199 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:be00(size=256) memory:fdeff000-fdefffff(prefetchable) memory:fdef8000-fdefbfff(prefetchable)
smithy@smithy-cnc:~$ 
mithy@smithy-cnc:~$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 50:e5:49:e1:f3:28  
          inet addr:192.168.1.199  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772 (2.7 KB)  TX bytes:2772 (2.7 KB)


smithy@smithy-cnc:~$ 
smithy@smithy-cnc:~$ **cat /etc/udev/rules.d/70-persistent-net.rules **
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x1106:0x3065 (via-rhine)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:30:18:ae:97:cc", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:35:48:15", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="6c:f0:49:5e:7d:d9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:35:48:13", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:38:46:90", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:e2:a7:8b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth5"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:6f:65:3d:2e:a5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth6"


# PCI device 0x1106:0x3065 (via-rhine)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:30:18:a6:cc:c6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth7"


# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:e1:f3:28", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth8"


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:e1:f3:28", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
smithy@smithy-cnc:~$ 
smithy@smithy-cnc:~$ 
smithy@smithy-cnc:~$** route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
smithy@smithy-cnc:~$ cat /etc/resolve.conf
nameserver 192.168.1.1
smithy@smithy-cnc:~$
mithy@smithy-cnc:~$ **cat /etc/network/interfaces **
auto eth0
iface eth0 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1
auto lo
iface lo inet loopback


smithy@smithy-cnc:~$ 

```

---

### Post by weatherman2 on 2015-04-26
Boot a live USB of a newer version of Ubuntu like 14.04.  See if the network connection is detected.

Look carefully at the ethernet jack on the back of the motherboard.  Take a picture of it and zoom in.  See if any of the pins are bent, making a connection difficult.

At worst, you can plug in another ethernet card in one of the expansion slots and use that for ethernet instead.

As for upgrading: start by making an image backup of your existing Ubuntu 10.04 installation (try Clonezilla).  Or, clone it to another spare hard drive.  Then try the upgrade on the spare (should be able to do an in-place upgrade to Ubuntu 12.04).  If that fails badly, then you know not to try that on the original drive; if it works on the clone, you are probably good to go with a real upgrade.  Ubuntu 12.04 LTS is supported until April 2017.  You might as well then try upgrading to 14.04 while you are at it and if you can get that to work, then you are good for another two years.

---

