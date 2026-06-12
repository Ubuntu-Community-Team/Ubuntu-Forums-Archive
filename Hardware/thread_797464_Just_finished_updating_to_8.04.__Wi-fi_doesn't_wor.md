---
title: "Just finished updating to 8.04.  Wi-fi doesn't work anymore"
date: 2008-05-17
forum: Hardware
---

### Post by NAYRB85 on 2008-05-17
I own a Dell Inspiron 640m laptop.  I updated to 8.04 and now the LED that indicates that wireless is on doesn't turn on anymore.  I tried setting the static IP or use DHCP but neither work.  Please help :(

---

### Post by balagosa on 2008-05-17
yeah, alot of people having trouble with their WiFi during upgrade.

can you post the outcomes of these:

```
lspci
```

```
lshw -C network
```

---

### Post by NAYRB85 on 2008-05-17
lspci yielded this:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 0a)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```


lshw -C network yielded this:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:47:d7:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.78 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:76:44:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

```

---

### Post by CPNowell on 2008-06-17
> **NAYRB85 said:**
> I own a Dell Inspiron 640m laptop.  I updated to 8.04 and now the LED that indicates that wireless is on doesn't turn on anymore.  I tried setting the static IP or use DHCP but neither work.  Please help :(
I had the same issue but cause the light was off, I didn't just assume it wasn't working (sounds a bit weird I know) so I let the system fully load and then clicked on the network icon in the notification panel (which was showing disconnected). I was right, it was working, just not showing any light. It was showing my AP as available so I just entered my WPA2 password and it works fine and at full speed just like before the Heron upgrade. Just no light. This is on an Acer Aspire 5612WLMi with iwl3945 driver loaded.

(rant=on) What is it with the Linux community? **This is why people get put off making the change to Linux!** Has no-one in that community heard of the expression "If it ain't broke, don't fix it!" This worked perfectly fine on this machine through the previous 3 major releases/updates and now it gets nuked! sheesh! (rant=off)

Colin

---

### Post by lian1238 on 2008-09-28
I like your ranting style. I feel the same way. I'm now waiting for 8.10. Had to skip 8.04 because of my wireless problem.

---

