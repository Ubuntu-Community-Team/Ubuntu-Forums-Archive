---
title: "Unable to get on line"
date: 2011-07-17
forum: Hardware
---

### Post by TXbirder on 2011-07-17
I have a new Acer Aspire 1830.  I have set it up as a dual-boot with Win7 Home and Unbutu 10.04. The Windows side works fine.  When I open Ubuntu I see the "**Welcome to Ubuntu 10.04 LTS**" page but I am unable to get on line with Ubuntu.  When I try, I get : **Server not found.  Firefox can't find the server at login.yahoo.com.**  Or at any other website I try. 
I can switch to Win7 and get on line with no trouble.  All other functions of Ubuntu that I have tried work OK.

This is using a Ethernet cable.  When I disconnect the Ethernet and try again, I  get the **Ubuntu Start Page**, instead of the **Welcome to Ubuntu 10.02 LTS** page, and can get on line immediately.  Why will my wired connection work fine with Win7 and not with Ubuntu?  Why does the wired connection lead me to the Welcome page instead of the Start page?


John

---

### Post by westie457 on 2011-07-17
> **TXbirder said:**
> I have a new Acer Aspire 1830.  I have set it up as a dual-boot with Win7 Home and Unbutu 10.04. The Windows side works fine.  When I open Ubuntu I see the "**Welcome to Ubuntu 10.04 LTS**" page but I am unable to get on line with Ubuntu.  When I try, I get : **Server not found.  Firefox can't find the server at login.yahoo.com.**  Or at any other website I try. 
I can switch to Win7 and get on line with no trouble.  All other functions of Ubuntu that I have tried work OK.

This is using a Ethernet cable.  When I disconnect the Ethernet and try again, I  get the **Ubuntu Start Page**, instead of the **Welcome to Ubuntu 10.02 LTS** page, and can get on line immediately.  Why will my wired connection work fine with Win7 and not with Ubuntu?  Why does the wired connection lead me to the Welcome page instead of the Start page?


John
Could open a terminal and run these commands
```
lspci

lshw -c network
```

then copy and paste the output in a new reply please.

---

### Post by TXbirder on 2011-07-17
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

john@john-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
john@john-laptop:~$ lshw -c
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by TXbirder on 2011-07-17
Sorry.  Incomplete entry in terminal.  Will do it again.
John

---

### Post by TXbirder on 2011-07-17
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

john@john-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
john@john-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d343ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:10:1a:6e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.68 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d240ffff
john@john-laptop:~$

---

### Post by westie457 on 2011-07-17
The answer to your problem is in this link. [http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)
Follow the instructions posted by chilli555 and it will work.

---

