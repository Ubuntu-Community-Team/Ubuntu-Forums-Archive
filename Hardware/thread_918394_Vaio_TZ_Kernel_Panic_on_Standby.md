---
title: "Vaio TZ Kernel Panic on Standby"
date: 2008-09-12
forum: Hardware
---

### Post by Numer0bis on 2008-09-12
Hello everybody

I searched the forum but couldn't really find anything similar to my problem.  I know Sony Vaio's aren't really the linux friendliest notebooks but I chose the vaio tz because of it's small size and long lasting battery. My Problem is whenever I want to put the notebook into standby or hibernate it end up with a kernel panic and the caps lock and scroll lock led start flashing. The only way I know of to restart that thing  is to remove the battery and unplug it from power. Has anyone any idea why that happens? Attached you can find a screen shot of the problem. Thanks for any help in advance

Numer0bis

---

### Post by IntuitiveNipple on 2008-09-13
Part of that back-trace has obviously scrolled off the screen so we can't see the precise function where the panic occurred. However, it does look to be network related; possibly the network driver kernel-module.

Can you attach a (compressed) copy of /var/log/dmesg so we know the start-up configuration of the system:
```

cat /var/log/dmesg | gzip dmesg.log.gz

```
In addition, report the results of:
```

lspci -nn

lsusb

sudo lshw -C network

```
I've run Sony Vaio notebooks and laptops for several years without major issues and find them to be reliable work-horses. As with all hardware though, it does help to research the Linux support for *problem* components such as 3D graphics chip-sets, web-cams and flash memory readers.

There are a number of known issues with suspend/resume that are usually due to incomplete or incorrect kernel module drivers. It can usually be solved by pre-unloading the driver via the PM (Power Management) scripts. 

For example, on this Vaio VGN-FE41Z:
```

cat /etc/pm/config.d/modules_unloads

SUSPEND_MODULES="iwl3945 r5u870 uvcvideo ehci_hcd"

```

---

### Post by Numer0bis on 2008-09-13
lspci -nn:
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
09:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
09:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
09:04.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)


```

lsusb:
```

Bus 005 Device 008: ID 054c:01bb Sony Corp. 
Bus 005 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 005 Device 006: ID 05ca:183a Ricoh Co., Ltd 
Bus 005 Device 002: ID 1b1c:1a90  
Bus 005 Device 003: ID 054c:0325 Sony Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 147e:2016  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```
sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:1a:80:d2:60:ba
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:02:8f:15


       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.6 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn


```

]
Temporary fix for the kernel panic: I upgraded my distribution via running update-manager -d to 8.10 alpha 5 and now suspend / hibernation works fine, even the new theme looks really good but now some programs which used to work fine on 8.04 don't work anymore like: Skype and keepassx. It seems that the new Kernel fixes most of the problems.

Greetz

Numer0bis

---

### Post by IntuitiveNipple on 2008-09-13
> 
unfortunately:
chris@vaiotz92:~$ cat /var/log/dmesg | gzip dmesg.log.gz
gzip: dmesg.log.gz: No such file or directory

so the first command didn't work.

Oops! My typing mistake... it should have been:
```

cat /var/log/dmesg | gzip > dmesg.log.gz

```
I'll look at the log-file see if there are clues.

---

### Post by IntuitiveNipple on 2008-09-13
If you are happy to remain with kernel 2.6.27 then we don't need to investigate further. I hope you can sort out the Intrepid issues more successfully :)

---

### Post by Numer0bis on 2008-09-13
yeah I'm quite happy with the new kernel. Everything works as expected. Suspend works really good. Put the laptop into suspend mode a couple of times. Worked flawlessly. And no usb error occures during the process of putting it into suspend. The only programs are that some of programs are not working anymore. I hope everything will be sorted out till the official release in october.

But Thanks for all the help.

---

