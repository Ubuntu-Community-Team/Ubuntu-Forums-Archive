---
title: "No Wireless extensions for Ubuntu 8.10 with intel 5100 AGN"
date: 2009-10-16
forum: Hardware
---

### Post by sibel1919 on 2009-10-16
Help. I'm a complete Ubuntu newbie but I've been trying to get ubuntu 8.10 to detect my intel 5100 wireless card but it's been three days now and nothing. I've tried installing the compat and iwlwifi 5000 packages and although I think i did everything right I'm still not recieving any signal at all. 

here's some details:

> ripley@sibel12:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Kernel modules: i2c-i801
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
    Kernel driver in use: r8169
    Kernel modules: r8169
08:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
    Kernel driver in use: ohci1394
    Kernel modules: ohci1394
08:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
    Kernel modules: sdhci-pci
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
after I run sudo make, install, ect.. I still get nothing..

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
Please someone help me out.

---

### Post by drsealion on 2009-10-16
It's a know bug in the kernel. An official patch has been made, but it is not yet in ubuntu repositories. All the information you need you can find it here -> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933")

---

### Post by Giblet5 on 2009-10-16
I got my 5100AGN to work for five minutes.

It was getting about "half" on the signal strength when sitting next to the AP.

The 5100AGN is a cheaper (and lower-power) version of the 4965AGN.

I ripped that 5100AGN POS out of my laptop and replaced it with a 4965AGN which was $24.95 & $3s+h from Tigerdirect. I sold the newer crap-card for $18.

$9 and I have the finest wifi receiver/AP made.

---

### Post by sibel1919 on 2009-10-16
I tried the kernel fix but still nothing at all. The only way i can get on the internet is through ethernet cable directly. Ubuntu still does not detect my card.

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:84:68:0c  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe84:680c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3036110 (3.0 MB)  TX bytes:596272 (596.2 KB)
          Interrupt:217 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)


---

### Post by sibel1919 on 2009-10-16
can anyone else help me please? Am I doing something wrong? I'm just about all out of options here, except maybe to buy a new card.

---

### Post by sibel1919 on 2009-10-17
Ok i tried to install the new kernel 2.6.29 deb files until i get to trying to install the image i get an error: Dependency is not satisfiable: wireless-crda

> Linux kernel image for version 2.6.29 on x86/x86_64
This package contains the Linux kernel image for version 2.6.29 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. i looked in synaptic for the meta package and its already installed, right now im on kernel 2.6.27
Any ideas??

UPDATE:

As for the 2.6.31 kernel when i try to install the 2nd head package i get another error: Dependncy is not satisfiable :lbc6

heeeeeeeeeeelp

---

### Post by sibel1919 on 2009-10-17
As for the 2.6.31 kernel when i try to install the 2nd head package i get another error: Dependncy is not satisfiable :lbc6

---

### Post by sibel1919 on 2009-10-17
thx dr lion i got it working finally, just had to find the package lcb6 and install the header, still said i needed it but i skipped to installing the image, it worked and now my wireless is being picked up, thanks so much maaan

---

