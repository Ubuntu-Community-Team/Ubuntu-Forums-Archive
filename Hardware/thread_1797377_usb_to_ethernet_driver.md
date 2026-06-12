---
title: "usb to ethernet driver"
date: 2011-07-05
forum: Hardware
---

### Post by Iqbal_ on 2011-07-05
Hi,
I have a usb to ethernet device no JP108:030818. Its driver is SR9600. Natty is on a 64 bits laptop.
When I insert this device in usb port of the laptop, thereafter I click on network manager icon, the device is shown. But the option is disabled.

When I lsmod a driver dm9601 is listed.

I want:
1- Where can I get the driver of this device from?
2- Any other solutions to make the device work.

Thank you

---

### Post by mikewhatever on 2011-07-05
Chances are, you don't need a second driver. why don't you backtrack and post the outputs of the following:
```

ifconfig

sudo lshw -C network

rfkill list all

```

---

### Post by Iqbal_ on 2011-07-05
Hi,
Output of the first two commands. The third command did not return anything.

eth0      Link encap:Ethernet  HWaddr 00:0f:fe:0b:f1:fc  
          inet addr:10.21.171.121  Bcast:10.21.171.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe0b:f1fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57312262 (57.3 MB)  TX bytes:1654230 (1.6 MB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 10:13:50:a8:51:ff               <---------Device in question 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31440 (31.4 KB)  TX bytes:31440 (31.4 KB)

  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:40:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:fe:0b:f1:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a ip=10.21.171.121 latency=0 multicast=yes
       resources: irq:17 memory:f0400000-f040ffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth2
       serial: 10:13:50:a8:51:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=dm9601 driverversion=22-Aug-2005 firmware=Davicom DM9601 USB Ethernet multicast=yes

The disk provided with the usb-adapter had SR9600 driver, which could not be "make".

---

### Post by mikewhatever on 2011-07-06
Sometimes, a device may be disabled through rfkill. Try **rfkill unblock eth2** .

---

