---
title: "Yet another wireless help thread."
date: 2009-02-25
forum: Hardware
---

### Post by jrela2000 on 2009-02-25
first my lspci
```
$ sudo lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

I was following these instructions

```
5.2 Wireless Broadcom

There is no native support for Broadcom wireless cards, however they work through the ndiswrapper workaround.

Jlandaw has written a comprehensive guide on this issue here: http://ubuntuforums.org/showpost.php?p=4808350

HP Pavilion Laptops with AMD Turion platform ship with a Broadcom wireless card. Unfortunately Broadcom is one of the least Linux friendly companies and in fact it does not provide any support for linux OSs (differently from e.g. Intel). Given this, support for linux is provided via ndiswrapper hack.

You can download the windows drivers here (these are for a Broadcom BCM 4328 but should work for all the series) then extract the archive in a folder you call broadcom in your home directory.

Install ndiswrapper and follow the procedure:

sudo apt-get install ndiswrapper-utils

sudo ndiswrapper -i $HOME/broadcom/DRIVER_EN/bcmwl5.inf

sudo ndiswrapper -l

sudo modprobe ndiswrapper

To make ndiswrapper automatically run at each startup:

sudo ndiswrapper -m

OR we can add ndiswrapper module to boot modprobed drivers

gksu cat ndiswrapper >> /etc/modules

At next bootup your Broadcom wireless card will be recognized!
```

When I try to get ndiswrapper I get:

```
:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate

```

So then I:

```
sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.2kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Fetched 20.2kB in 0s (33.8kB/s)           
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 116484 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...

```

Cool, but:

```
 sudo ndiswrapper -i $HOME/broadcom/DRIVER_EN/bcmwl5.inf
Error: no ndiswrapper utils found!

```

so now I'm stuck.....

---

### Post by Flyingjester on 2009-02-25
isn't your card atheros?

---

### Post by jrela2000 on 2009-02-25
yes. but it is not working. I updated setting in the network config.  Its a no go.

---

### Post by Flyingjester on 2009-02-25
no i mean, why are you using a broadcom guide to get an atheros card working?

---

### Post by jrela2000 on 2009-02-25
I don't know.  Because I cant get the Atheros card working?

---

### Post by Flyingjester on 2009-02-25
that doesn't make sense... a broadcom guide will not help you get you started with atheros wireless.. however i did a search of this site and came up with a guide for your card. enjoy
[http://ubuntuforums.org/showthread.php?t=1078830&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=1078830&highlight=AR242x)

---

### Post by jrela2000 on 2009-02-25
thx. how do I marked as solved?

---

### Post by Flyingjester on 2009-02-25
thread tools at the top, and click marked as solved, glad i could help :)

---

### Post by stchman on 2009-02-25
Amazing, not to bash the OP, but there are Ubuntu bashers that will put Ubuntu down when they have ZERO idea what they are doing.

---

### Post by binbash on 2009-02-25
[http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html)

---

