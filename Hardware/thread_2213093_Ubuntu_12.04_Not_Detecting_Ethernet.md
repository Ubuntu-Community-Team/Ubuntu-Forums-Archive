---
title: "Ubuntu 12.04 Not Detecting Ethernet"
date: 2014-03-24
forum: Hardware
---

### Post by James_Kiel on 2014-03-24
Hello, I have been using Linux on and off for the past few years while going to college for Software Engineering, so I am familiar with most of the features in ubuntu.  I have just updated my old PC server from XP to Ubuntu 12.04 lts.  After the install was complete, the computer stopped detecting my Ethernet connection.  After looking around the forums at different threads, I have not found one similar to my situation.  
The current status is: 

                      1) Does detect my Ethernet card
                      2) Does not detect my Ethernet connection 
3) Tested cable with another PC and verified the cable is working
                      3) I have plugged in a USB wireless network adapter to test and it works. 

What am I missing here?

Thanks in advance!

---

### Post by Iowan on 2014-03-24
Please post results of ```
sudo lshw -C network
```
I presume you're using the server version of Ubuntu 12.04 (no Network Manager)
Are you set up for DHCP address, or are you using a static address?
Post contents of */etc/network/interfaces* and results of ```
ifconfig -a
```

---

### Post by varunendra on 2014-03-24
Welcome to the forums James!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lsb_release -d
sudo lshw -C network
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

**EDIT:** Oops! The "Boss" is here, posting simultaneously :p

---

### Post by James_Kiel on 2014-03-24
I am not using the server version out of lack of familiarity,  even though I plan to host a http and ftp server on it as well as others.  If needed I would give it a shot.  I am using DHCP and have assigned it its own internal address based off of the mac address.
 
[HR][/HR] No return for sudo lshw -C network

[HR][/HR][COLOR=#000000][FONT=Ubuntu Mono]
For ifconfig -a

```
lo                 Link encap:Local Loopback
                   inet addr:127.0.0.1 Mask: 255.0.0.0
                   inet6 addr: ::1/128 Scope:Host
                   UP LOOPBACK RUNNING MTU: 65536   Metric:1
                   RX packets: 897 errors: 0 dropped:0 overruns:0 frame:0
                   TX packets: 897 errors: 0 dropped:0 overruns: 0 carrier:0
                   collisions:0 txqueuelen:0
                   RX bytes: 80938 (80.9 KB)     TX bytes:80938 (80.9 KB)
```
[/FONT][/COLOR]

---

### Post by Iowan on 2014-03-24
No crime in using a desktop version...or a static lease ( I have a few machines set up that way).
If you're using Network Manager, you will want to verify "Connect automatically" is checked.

---

### Post by James_Kiel on 2014-03-24
Yes the Wired Connection is checked.

---

### Post by varunendra on 2014-03-24
> **James_Kiel said:**
> No return for sudo lshw -C network

It'll take some time to grab the info and display it. Give the command a few seconds to complete its job. :)

**PS:**
'Code' tag wasn't done correctly, please check out the "Use Code Tags" link in my signature again. :)

---

### Post by James_Kiel on 2014-03-24
Thanks for the "code tag" tip.  I have run ```
 sudo lshw -C network 
``` several times and it does not display an output.

---

### Post by varunendra on 2014-03-24
Hmm.. I kinda suspected that assuming you had run "ifconfig -a", not just "ifconfig".

Have you checked the BIOS to make sure the network interfaces are detected and enabled there? If yes, please post the output of -
```
grep -i 'eth' /var/log/syslog | tail -20
```
..preferably, immediately after a fresh boot.

---

### Post by James_Kiel on 2014-03-24
After entering:

Input:
```
 grep -i 'eth' /var/log/syslog | tail -20 
```

Output:
```
 
Mar 24 19:26:22 Vandalay NetworkManager[779]: <info> (eth1): preparing device.
Mar 24 19:26:22 Vandalay NetworkManager[779]: <info> (eth1): deactivating device (reason 'managed') [2]
Mar 24 19:26:22 Vandalay kernel: [   20.565966] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 24 19:26:22 Vandalay kernel: [   20.567339] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 24 19:30:36 Vandalay kernel: [   17.428941] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 24 22:00:05 Vandalay kernel: [    1.924802] e100 0000:01:08.0 eth0: addr 0xfeaff000, irq 20, MAC addr 00:13:20:d4:5d:1f
Mar 24 22:00:05 Vandalay kernel: [    6.474788] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 24 22:00:10 Vandalay kernel: [   17.048464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 24 22:00:13 Vandalay NetworkManager[781]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth1, iface: eth1)
Mar 24 22:00:13 Vandalay NetworkManager[781]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth1, iface: eth1): no ifupdown configuration found.
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): carrier is OFF
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): new Ethernet device (driver: 'e100' ifindex: 2)
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): now managed
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): bringing up device.
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): preparing device.
Mar 24 22:00:13 Vandalay NetworkManager[781]: <info> (eth1): deactivating device (reason 'managed') [2]
Mar 24 22:00:13 Vandalay kernel: [   20.429956] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 24 22:00:13 Vandalay kernel: [   20.431355] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
james@Vandalay:~$ 


```

---

### Post by varunendra on 2014-03-24
Interesting! The device is clearly detected. I wonder if you are running "lshw" correctly. Do you get any error on the screen when running the command? Do you get any output with this -
```
lshw
```??

Please post the outputs of the following -
```
nm-tool
lspci -nnk | grep -iA2 net
```

If the above doesn't show the Ethernet interface, then full output of -
```
lspci -nn
```

---

### Post by James_Kiel on 2014-03-25
Input ```
 lshw 
```

Output 
```

vandalay                  
    description: Mini Tower Computer
    product: Dell DE051
    vendor: Winbond Electronics
    serial: FLBL091
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-4C00-1042-804C-C6C04F303931
  *-core
       description: Motherboard
       product: 0CF458
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN708215B7A232.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A00
          date: 08/15/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Microprocessor
          size: 2666MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 1
             slot: DIMM_2
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:3
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth1
                version: 02
                serial: 00:13:20:d4:5d:1f
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:feaff000-feafffff ioport:df40(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST380011A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8.16
             serial: 5JVV76Q4
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00024189
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f1d59ecd-6766-449c-9e2c-9ed873d38d59
                size: 74GiB
                capacity: 74GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-03-23 20:18:34 filesystem=ext4 lastmountpoint=/ modified=2014-03-23 20:36:45 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-03-24 22:00:01 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 502MiB
                capacity: 502MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 502MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRW/DVD GCC4482
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: E107
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=74055729
           *-volume:0 UNCLAIMED
                description: EFI GPT partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                capacity: 200MiB
                capabilities: primary nofs
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/G-DRIVE #1
                version: 3.1
                serial: dcddb06a-7bfb-1145-88ac-6f5874388a66
                size: 1862GiB
                capacity: 1862GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-10-24 17:32:53 filesystem=ntfs label=G-DRIVE #1 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted

```

Input
```

nm-tool

```

Output
```

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:13:20:D4:5D:1F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

Input
```

slpci -nnk | grep -iA2 net

```

Output
```

01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: Dell Device [1028:01d5]
    Kernel driver in use: e100

```

Input
```

lspci

```

Output
```

00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)

```

---

### Post by James_Kiel on 2014-03-25
It might also help to note that I am using an aftermarket Encore Network Card,  I don't see that anywhere in the logs.

---

### Post by varunendra on 2014-03-25
As a quick blind shot, please try this first -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Reboot and check if some pleasant magic happens. Most probably there won't be any, in which case try the following -

While being connected to internet with your USB wireless adapter, install 'ethtool' -
```
sudo apt-get install ethtool
```

Run "**nm-tool**" command again to confirm whether your Ethernet interface is now "**eth0**" or still "**eth1**". Assuming it would now be "**eth0**", run the following command to force 100 Mb/s Full duplex mode on it -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Then check -
```
sudo ethtool eth0
```
And notice the last line of the output. Does it show "Link detected" as "yes" now? If not, try the previous ethtool command with "speed 10" again. If none of these help, please post the outputs of -
```
sudo ethtool eth0
sudo lshw
```
..with the above tweak applied (speed 10, duplex full, autoneg off).

**EDIT:**
Just noticed your last comment about the external card. I strongly suggest you pull it out from the system before trying above. If it makes the onboard one work, we may then try it later.

**EDIT2:** By the way, if you have more secrets, it might be a good time to disclose them to save us from wasting time on 'Wondering & Guessing' :p

---

### Post by James_Kiel on 2014-03-25
It completely slipped my mind about mentioning it sorry.  But I do not have an onboard ethernet capability, thus the use of a PCI network card for the past 10 years.  

Here's the next set of data

Input
```

sudo ethtool eth0

```

Output
```

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: off
    Supports Wake-on: g
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: no

```

Input
```

sudo lshw

```

Output
```

vandalay                  
    description: Mini Tower Computer
    product: Dell DE051
    vendor: Winbond Electronics
    serial: FLBL091
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-4C00-1042-804C-C6C04F303931
  *-core
       description: Motherboard
       product: 0CF458
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN708215B7A232.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A00
          date: 08/15/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Microprocessor
          size: 2666MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 1
             slot: DIMM_2
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:3
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:13:20:d4:5d:1f
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=off broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:feaff000-feafffff ioport:df40(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST380011A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8.16
             serial: 5JVV76Q4
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00024189
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f1d59ecd-6766-449c-9e2c-9ed873d38d59
                size: 74GiB
                capacity: 74GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-03-23 20:18:34 filesystem=ext4 lastmountpoint=/ modified=2014-03-23 20:36:45 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-03-25 22:15:11 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 502MiB
                capacity: 502MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 502MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRW/DVD GCC4482
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: E107
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=74055729
           *-volume:0 UNCLAIMED
                description: EFI GPT partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                capacity: 200MiB
                capabilities: primary nofs
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/G-DRIVE #1
                version: 3.1
                serial: dcddb06a-7bfb-1145-88ac-6f5874388a66
                size: 1862GiB
                capacity: 1862GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-10-24 17:32:53 filesystem=ntfs label=G-DRIVE #1 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: f8:1a:67:1c:fd:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.11.0-15-generic firmware=1.3 ip=10.0.1.83 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by varunendra on 2014-03-26
Apart from two more suggestions, I think I'm out of ideas -

1) Try resetting the BIOS assuming it may be a problem of a stuck firmware or accidental change in IRQs.

2) Try a different card assuming the card is gone.

---

