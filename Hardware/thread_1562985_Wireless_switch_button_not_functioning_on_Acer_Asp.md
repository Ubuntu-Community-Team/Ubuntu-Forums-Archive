---
title: "Wireless switch button not functioning on Acer Aspire 4330 Laptop"
date: 2010-08-28
forum: Hardware
---

### Post by Gerant on 2010-08-28
Running 10.04 ubuntu, installed from USB, everything worked fine until I restarted. 
Wireless card: 
Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express)

---

### Post by pytheas22 on 2010-08-29
Please post the output of these commands, with the device plugged in:
```

lshw -C Network
lsusb
uname -rm
```

---

### Post by Gerant on 2010-08-29
georc@Ashen-Hymn:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:56700000-5670ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:cb:43:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:29 ioport:2000(size=256) memory:52410000-52410fff(prefetchable) memory:52400000-5240ffff(prefetchable) memory:52420000-5242ffff(prefetchable)
georc@Ashen-Hymn:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
georc@Ashen-Hymn:~$ uname -rm
2.6.32-24-generic i686


The usb device is my boot USB, the switch button for my Wireless card isn't working. The light isn't on and pressing it does nothing.

---

### Post by pytheas22 on 2010-08-29
The driver for this device should be included in Ubuntu.  It's possible the driver is simply not activated for some reason.  If you type:
```

sudo modprobe ath9k
sudo ifconfig wlan0 up
```

and wait a few seconds, does the wireless come up?  If so, it should be an easy fix to make this work automatically.

Also, it would be helpful to see the output of one more command, namely:
```

lspci -nn
```

Finally, to clarify, the wireless worked fine the first time you booted into Ubuntu?

---

### Post by Gerant on 2010-08-29
YOU ARE MY NEW GOD!!!!! 
LINUX WITCHDOCTOR! 
I LOVE YOU!:D:D:D
The first set of commands worked, it's up and connected now, thanks. 
I'm really new to linux so this was a learning experience. Thank you so much. 
Gosh, that was so easy, I feel dumb. Do you still want the output from lspci -nn? If so, it's 
 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
07:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
07:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
07:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
07:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

---

### Post by pytheas22 on 2010-08-30
Glad that worked :)  Run this command once:
```

echo ath9k | sudo tee -a /etc/modules
```

and from now on your wireless card should always "just work" whenever you restart the computer, without you having to type any commands.  Let me know if you have any trouble.

---

### Post by Gerant on 2010-08-30
/ect/modules Doesn't exist. D:

---

### Post by pytheas22 on 2010-08-31
It's /etc/modules--not /ect/modules :)

---

### Post by Gerant on 2010-08-31
..... I'm retarded. :D XD

---

