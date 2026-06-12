---
title: "Ubuntu 12.04 Kernel Panic wireless?"
date: 2012-09-02
forum: Hardware
---

### Post by andyawesomeayer on 2012-09-02
I just installed a copy of ubuntu on a new ssd (dual booting with windows 7) and am having some trouble, first of all when installing it kept crashing when it got passed the part where you put in your location and hit continue(I believe from it trying to download). crashed a couple times so I did the alternate install and it starts up great but when i enable my wireless card and connect I get a kernel panic after 5-10 minutes or immediately after I try to download something.... Any help would be much appreciated I know I need to give you guys some more specific info but I'm kinda a newb but 
lspci -vnn gives me:

04:07.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Flags: bus master, fast devsel, latency 32, IRQ 21
    Memory at fdcfc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules: wl, ssb

---

### Post by andyawesomeayer on 2012-09-03
thought I would add some more info

$ lsb_release -d
 > Description:    Ubuntu 12.04.1 LTS$ uname -mr
> 3.2.0-29-generic x86_64$  lspci -vnn | grep -C 10 road
> 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at ce00 [size=256]
    Memory at fdeff000 (64-bit, prefetchable) [size=4K]
    Memory at fdef8000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:07.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Flags: bus master, fast devsel, latency 32, IRQ 21
    Memory at fdcfc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules: wl, ssb$ lsmod | egrep 'b43|bc|bm|wl|ssb|xx'
> wl                   2568210  0 
lib80211               14381  2 lib80211_crypt_tkip,wl$ dmesg | egrep 'b43|bc|bm|wl|ssb|xx'
> [    0.555503] usbcore: registered new interface driver usbfs
[    0.555503] usbcore: registered new interface driver hub
[    0.555503] usbcore: registered new device driver usb
[    1.584125] usbcore: registered new interface driver libusual
[    1.855514] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.855516] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.034386] usbcore: registered new interface driver usbhid
[    2.430435] wl 0000:04:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21$ sudo lshw -C network
> PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:bd:87:05
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.54 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fdef8000-fdefbfff
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth2
       version: 01
       serial: e0:91:f5:65:dc:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=32 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:21 memory:fdcfc000-fdcfffffhope this helps

$ dmesg | tail -l
> [    4.011795] [fglrx] Gart USWC size:1280 M.
[    4.011797] [fglrx] Gart cacheable size:508 M.
[    4.011800] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[    4.011802] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[    4.011803] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   36.043184] r8169 0000:03:00.0: eth0: link up
[   36.043775] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   46.680050] eth0: no IPv6 routers present
[   53.742990] audit_printk_skb: 39 callbacks suppressed
[   53.742992] type=1400 audit(1346656273.631:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2087 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


---

### Post by andyawesomeayer on 2012-09-03
Well it seems that I have solved the issue, I'll play around for the rest of the night then change to solved if I don't have anymore problems. I reverted back to the b43 drivers and all seems to be well

Here is what I did

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer

---

