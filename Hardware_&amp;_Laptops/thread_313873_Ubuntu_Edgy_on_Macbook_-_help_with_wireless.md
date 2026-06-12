---
title: "Ubuntu Edgy on Macbook - help with wireless?"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by sooperhooper on 2006-12-06
I recently partitioned my hard drive and installed Ubuntu on it; I'm now successfully dual booting OS X and Ubuntu "Edgy" on my 2.0 GHz Core Duo (*not*  Core 2 Duo) MacBook. Problem is, I can't get my wireless card to work in Ubuntu. I know this is a common problem, and I'll pre-emp all of the "use the search function!" responses by saying that I already have, and of the threads I've read, they either didn't my problem for me, or I didn't have enough of a grasp on the directions to execute them. Bear in mind this is my first experience with Linux at all, so I might need some assistance in the most elementary of issues, haha.

Furthermore, I do not have a wired ethernet connection available to me, generally - I have been relying solely on airport wireless for my internet connection for the past three months or so. This has made troubleshooting in Ubuntu a tedious experience, as I've had to jump back and forth between OSes to read or download something and then go try it out.

I tried running a few terminal commands that I discovered in other troubleshooting threads so I could provide some background. Here's what I've got:

```

dan@dan:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp


dan@dan:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:F2:27:09:BF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


dan@dan:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:27:09:bf
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:90200000-90203fff ioport:1000-10ff irq:177
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:90100000-9010ffff irq:11
  *-usb
       description: Bluetooth wireless interface
       vendor: Apple Computer, Inc.
       physical id: 1
       bus info: usb@4:1
       version: 19.65
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s


dan@dan:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


dan@dan:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
dan@dan:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)


dan@dan:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:17:f2:27:09:bf arp 1
ath0 mac 00:17:f2:43:78:95 arp 1
```

The difference I'm seeing between my case and some others I've read is that my wireless card is a)listed as an ethernet controller and b)not present in a number of fields where it would've shown up for other people.

Anyone willing to give a noobie a hand?

---

### Post by sooperhooper on 2006-12-08
Bump? Anyone?

---

### Post by moaxey on 2006-12-24
I'm a huge ubuntu fan, but its hard to convince others as theres always a few little things that are trapped... on the macbook though I have made progress that I never have before.

i've never got wireless working on any machine, the dell i had had broadcom chips and i was all excited about the new kernel in edgy, nothing changed though.

totally stuck on wireless on macbook. The card is not recognised at all, doesnt appear in the networking panel. here is the output of lspci

```
mjoakes@mjoakes-macbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

so i guess its the Atheros Communications Unknown device.

all the instructions i've read before (and i've tried a lot on previous machines) start with a recognised card.

then i found this post on another site, with an almost exact description of my problem

[http://www.linuxquestions.org/questions/showthread.php?p=2521574](http://www.linuxquestions.org/questions/showthread.php?p=2521574)

Which points to the madwifi package as a way of getting atheros cards working in linux.

Searching for madwifi in synaptic I found that it is included in the restricted kernel modules package,,,

and that the default edgy installation had included the 386_64 bit version... and as far as I am aware, core2duo is still 32 bit.

and i'm just about to restart to load the new kernel modules to see if it worked!

and it didnt...

---

### Post by moaxey on 2006-12-24
found the answer here

[http://ubuntuforums.org/showthread.php?p=1822454#post182245](http://ubuntuforums.org/showthread.php?p=1822454#post182245)

---

