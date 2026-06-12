---
title: "Weak Wifi with Intel Centrino Wireless-n 1000 on 10.10"
date: 2011-03-27
forum: Hardware
---

### Post by Dmeni on 2011-03-27
Hi everybody,
I've recently bought the new Dell XPS 15 L502x and installed 10.10 64bit.
Everything seems to run fine except for the wifi (and the graphic card which I hope I can resolve later).

It keeps disconnecting every few minutes and the bit rate is really poor.

here's the output of some comands to give you an idea

this is the output of lspci showing the recognised Wireless Card
```

$ lspci | grep Network
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

```

$ iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wwan0     no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"freebox_BOR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 92:43:C1:38:41:8C   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:18   Missed beacon:0

```

the bitrate is barely at 1 Mb/s and I've rarely seen it at 2 Mb/s

from $ rfkill list I can see nothing is blocked

```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


and finally the output from $ hwinfo --netcard

```

24: PCI 300.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_83
  Unique ID: y9sn.7ENUz3zhXm0
  Parent ID: qTvu.AnbCFkUXWo0
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel WLAN controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0083 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1325 
  Driver: "iwlagn"
  Driver Modules: "iwlagn"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf1b00000-0xf1b01fff (rw,non-prefetchable)
  IRQ: 50 (48280 events)
  HW Address: 8c:a9:82:4a:b0:0a
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00000083sv00008086sd00001325bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlagn is active
    Driver Activation Cmd: "modprobe iwlagn"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

26: PCI 600.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8168
  Unique ID: rBUF.iHyiMM6h1ED
  Parent ID: HnsE.I59C5EnOkR2
  SysFS ID: /devices/pci0000:00/0000:00:1c.5/0000:06:00.0
  SysFS BusID: 0000:06:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x050e 
  Revision: 0x06
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xf1804000-0xf1804fff (ro,non-prefetchable)
  Memory Range: 0xf1800000-0xf1803fff (ro,non-prefetchable)
  IRQ: 46 (3944 events)
  HW Address: 14:fe:b5:9c:05:6c
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00001028sd0000050Ebc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

```

I really don't know what could be possibily wrong. the kernel version is 2.6.35-28-generic and I've installed the linux-backport-modules-compat-wireless-2.6.37-2.6.35-28-generic.

I've tried with wicd but the results were the same if not worse so I removed it.

I've also tried enabling the bgn mode as suggested by this thread.
[http://ubuntuforums.org/showthread.php?t=1592846](http://ubuntuforums.org/showthread.php?t=1592846)
but nothing really changed for me.

I thank you in advace
Dmeni

---

### Post by Dmeni on 2011-03-28
No one? :(

---

### Post by vl_ado on 2011-04-17
I have the same wireless card. I can't make it work with aireplay-ng and also with kismet. Unable to change channel manually either. 2 programs having the same issue i think is the drivers and not the software. I really need help with this. Probably that the hardware is still to new for Linux :(.

---

### Post by Ghostmn on 2011-04-17
Your wifi card has been supported since 2.6.30, there might have been some regression since then. Try installing 2.6.36 (both Amd64)  from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/) 

It May or may not resolve your problem.

---

