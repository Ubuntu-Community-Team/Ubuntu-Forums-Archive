---
title: "Network and Video Card Conflict"
date: 2008-11-03
forum: Hardware
---

### Post by rmccarri on 2008-11-03
Hi,
I've had this problem with Ubuntu 7.10, but upgrading to 8.04 fixed it.  Now it's back with 8.10.

If I install the nVidia proprietary drivers, my integrated network connection stops working.  It grabs an IP address and everything, but it will not even ping any outside connections.  Presumably, this might be an IRQ conflict or something?  Has anyone else seen this behavior or does anyone have any suggestions as to where to start diagnosing this problem?
Thanks!
Rob

---

### Post by phidia on 2008-11-03
It would be helpful to have all the hardware specifics and how you installed the nvidia driver.

Did you use Hardware drivers from System > Admin to enable the graphic driver?
If you did and then lost your network it sounds like you have a reportable bug.

What does "lshw -C network" & "iwconfig" output?

---

### Post by prshah on 2008-11-03
> **rmccarri said:**
> Presumably, this might be an IRQ conflict or something?  
any suggestions as to where to start diagnosing this problem?


Can you post the outputs to the following Terminal (Applications-Accessories-Terminal) commands both _before_ and _after_ installing the proprietary drivers?

```

cat /proc/interrupts
dmesg | grep -i eth0
```

---

### Post by rmccarri on 2008-11-05
Hi, thanks for the replies.  Here is the requested information!  I hope that it helps someone figure out what's causing the conflict!

[B]
With nVidia Installed:[/B]

*# lshw -C network*
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:1a:92:09:24:72
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:14:26:f1:29:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[I]
# iwconfig[/I]
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


*# ifconfig*
eth0      Link encap:Ethernet  HWaddr 00:1a:92:09:24:72  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe09:2472/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:46 overruns:0 frame:0
          TX packets:47 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1815 (1.8 KB)  TX bytes:6595 (6.5 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4198 (4.1 KB)  TX bytes:4198 (4.1 KB)

[I]
# cat /proc/interrupts[/I]
           CPU0       
  0:        115   IO-APIC-edge      timer
  1:        563   IO-APIC-edge      i8042
  8:          2   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:      32118   IO-APIC-edge      i8042
 14:       3832   IO-APIC-edge      pata_via
 15:          0   IO-APIC-edge      pata_via
 17:       1551   IO-APIC-fasteoi   HDA Intel
 20:          0   IO-APIC-fasteoi   uhci_hcd:usb1
 21:      26597   IO-APIC-fasteoi   uhci_hcd:usb3, ahci
 22:       7535   IO-APIC-fasteoi   uhci_hcd:usb2, ehci_hcd:usb5
 23:     100010   IO-APIC-fasteoi   uhci_hcd:usb4, eth0
 24:      22234   IO-APIC-fasteoi   nvidia
NMI:          0   Non-maskable interrupts
LOC:      27581   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

[I]
# dmesg | grep -i eth0[/I]
[    3.920751] eth0: VIA Rhine II at 0xfdffd000, 00:1a:92:09:24:72, IRQ 23.
[    3.921458] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   20.070396] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   32.492015] eth0: no IPv6 routers present
[   90.816035] NETDEV WATCHDOG: eth0 (via-rhine): transmit timed out
[   90.816650] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[   90.817292] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  361.000158] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
[  361.000803] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  375.000154] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  375.000798] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

[B]
Without the nVidia Drivers installed:[/B]
[I]
# lshw -C network[/I]
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:1a:92:09:24:72
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:b1:d0:26:f8:85
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

*# iwconfig*
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

*# ifconfig*
eth0      Link encap:Ethernet  HWaddr 00:1a:92:09:24:72  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe09:2472/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:584808 (584.8 KB)  TX bytes:190288 (190.2 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:202173 (202.1 KB)  TX bytes:202173 (202.1 KB)
[I]
# cat /proc/interrupts[/I]
           CPU0       
  0:        115   IO-APIC-edge      timer
  1:        485   IO-APIC-edge      i8042
  8:          2   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:      24522   IO-APIC-edge      i8042
 14:       2992   IO-APIC-edge      pata_via
 15:          0   IO-APIC-edge      pata_via
 17:       1610   IO-APIC-fasteoi   HDA Intel
 20:          0   IO-APIC-fasteoi   uhci_hcd:usb1
 21:      25867   IO-APIC-fasteoi   ahci, uhci_hcd:usb3
 22:       5854   IO-APIC-fasteoi   uhci_hcd:usb2, ehci_hcd:usb5
 23:       1459   IO-APIC-fasteoi   uhci_hcd:usb4, eth0
NMI:          0   Non-maskable interrupts
LOC:      30712   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0
[I]
# dmesg | grep -i eth0[/I]
[    6.269041] eth0: VIA Rhine II at 0xfdffd000, 00:1a:92:09:24:72, IRQ 23.
[    6.269750] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   19.996401] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.488011] eth0: no IPv6 routers present

---

### Post by rmccarri on 2008-11-06
Also, if it helps, I tried both the 173 and 177 versions of the nVidia driver from the gui drivers interface.  The video card is a EVGA GeForce 7300 LE 256MB PCIe.
Thanks!

---

### Post by prshah on 2008-11-06
> **rmccarri said:**
> ```

[   90.816035] NETDEV WATCHDOG: eth0 (via-rhine): transmit timed out
[   90.816650] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...

```

As per [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159980"), adding the "irqpoll" to your kernel parameter should help.

To check (make the change temporarily): when booting, press esc to enter the GRUB menu; scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add the word
```

irqpoll
```

then press enter; then "b" to boot.

If it works, post back on how to make it permanent. Note that in some cases, irqpoll can cause a performance hit; if you find it significant, then we should look for another solution to this problem.

If there's a problem, just reboot and you'll be back to normal.

---

### Post by rmccarri on 2008-11-10
Thanks!  Adding irqpoll to the startup options fixed the problem.  I went ahead and added it permanently to the /boot/grub/menu.lst file.

---

