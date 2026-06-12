---
title: "Wired ethernet Asus K50C Realtek 8168/8111"
date: 2010-08-13
forum: Hardware
---

### Post by mario64 on 2010-08-13
Hi and first of all sorry for my english.

I bought a laptop Asus k50c and i have problem with wired connection (wifi works fine). Ubuntu 10.04 load r8169 module for this card and i cant link detected. I can see some progress when i use official module from the realtek webpage (r8168-8.018) - link was detected but still i cant connect to the network.

ethtool eth0
```


Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: ug
    Current message level: 0x00000033 (51)
    Link detected: yes

```ethtool -i eth0
```

driver: r8168
version: 8.018.00-NAPI
firmware-version: 
bus-info: 0000:03:00.0

```lspci -vv 
```

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 27
    Region 0: I/O ports at ec00 [size=256]
    Region 2: Memory at febff000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [48] Vital Product Data <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0100c  Data: 4161
    Capabilities: [60] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <128ns, L1 unlimited
            ExtTag+ AttnBtn+ AttnInd+ PwrInd+ RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 4096 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [84] Vendor Specific Information <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [12c] Virtual Channel <?>
    Capabilities: [148] Device Serial Number 00-e0-4c-68-00-00-00-16
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8168
    Kernel modules: r8168

```lshw -c network
```

*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 48:5b:39:44:6b:61
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.018.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 ioport:ec00(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)

```ifconfig eth0
```

eth0      Link encap:Ethernet  HWaddr 48:5b:39:44:6b:61  
          inet6 addr: fe80::4a5b:39ff:fe44:6b61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x2000 


```dhclient eth0
```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/48:5b:39:44:6b:61
Sending on   LPF/eth0/48:5b:39:44:6b:61
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```uname -a 
```

Linux laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

```What i tried:
- RedFlag 6.2 (linux distro) works with this card  - using an old version of driver (r8168-8.009) and old kernel version ~2.6.27. On the  newer version  of the kernel I cant compile this old driver. 
- [COLOR=#000000]static network configuration does not help[/COLOR]
- other versions of the driver, which can compile a new kernel


When i try compile old driver:
```

make -C src/ clean
make[1]: Wej&#347;cie do katalogu `/home/uczen/r8168-8.009.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Opuszczenie katalogu `/home/uczen/r8168-8.009.00/src'
make -C src/ modules
make[1]: Wej&#347;cie do katalogu `/home/uczen/r8168-8.009.00/src'
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/uczen/r8168-8.009.00/src modules
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/uczen/r8168-8.009.00/src/r8168_n.o
/home/uczen/r8168-8.009.00/src/r8168_n.c: In function ‘rtl8168_init_one’:
/home/uczen/r8168-8.009.00/src/r8168_n.c:2897: error: ‘struct net_device’ has no member named ‘open’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2898: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2899: error: ‘struct net_device’ has no member named ‘get_stats’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2901: error: ‘struct net_device’ has no member named ‘stop’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2902: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2903: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2907: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2908: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2909: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/uczen/r8168-8.009.00/src/r8168_n.c:2922: error: ‘struct net_device’ has no member named ‘poll_controller’
/home/uczen/r8168-8.009.00/src/r8168_n.c: In function ‘rtl8168_open’:
/home/uczen/r8168-8.009.00/src/r8168_n.c:3014: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:117: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
/home/uczen/r8168-8.009.00/src/r8168_n.c: In function ‘rtl8168_interrupt’:
/home/uczen/r8168-8.009.00/src/r8168_n.c:4560: error: implicit declaration of function ‘netif_rx_schedule_prep’
/home/uczen/r8168-8.009.00/src/r8168_n.c:4561: error: implicit declaration of function ‘__netif_rx_schedule’
/home/uczen/r8168-8.009.00/src/r8168_n.c:4594: error: expected expression before ‘)’ token
/home/uczen/r8168-8.009.00/src/r8168_n.c:4594: warning: ‘return’ with a value, in function returning void
/home/uczen/r8168-8.009.00/src/r8168_n.c: In function ‘rtl8168_poll’:
/home/uczen/r8168-8.009.00/src/r8168_n.c:4615: error: implicit declaration of function ‘netif_rx_complete’
/home/uczen/r8168-8.009.00/src/r8168_n.c: In function ‘rtl8168_down’:
/home/uczen/r8168-8.009.00/src/r8168_n.c:4636: warning: unused variable ‘poll_locked’
make[3]: *** [/home/uczen/r8168-8.009.00/src/r8168_n.o] Error 1
make[2]: *** [_module_/home/uczen/r8168-8.009.00/src] Error 2
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [modules] Error 2
make[1]: Opuszczenie katalogu `/home/uczen/r8168-8.009.00/src'
make: *** [modules] Error 2

```

When i use kernel source from RedFlag distro (edit KDIR in makefile):
```

make -C src/ clean
make[1]: Wej&#347;cie do katalogu `/home/uczen/r8168-8.009.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Opuszczenie katalogu `/home/uczen/r8168-8.009.00/src'
make -C src/ modules
make[1]: Wej&#347;cie do katalogu `/home/uczen/r8168-8.009.00/src'
make -C /usr/src/2.6.27.10-1-i686 SUBDIRS=/home/uczen/r8168-8.009.00/src modules
make[2]: Wej&#347;cie do katalogu `/usr/src/2.6.27.10-1-i686'
  CC [M]  /home/uczen/r8168-8.009.00/src/r8168_n.o
/home/uczen/r8168-8.009.00/src/r8168_n.c: In function ‘rtl8168_down’:
/home/uczen/r8168-8.009.00/src/r8168_n.c:4636: warning: unused variable ‘poll_locked’
/home/uczen/r8168-8.009.00/src/r8168_n.c: At top level:
/home/uczen/r8168-8.009.00/src/r8168_n.c:2547: warning: ‘rtl8168_phy_power_down’ defined but not used
/home/uczen/r8168-8.009.00/src/r8168_n.c:3974: warning: ‘rtl8168_reinit_task’ defined but not used
  LD [M]  /home/uczen/r8168-8.009.00/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
/bin/sh: scripts/mod/modpost: not found
make[3]: *** [__modpost] B&#322;&#261;d 127
make[2]: *** [modules] B&#322;&#261;d 2
make[2]: Opuszczenie katalogu `/usr/src/2.6.27.10-1-i686'
make[1]: *** [modules] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/uczen/r8168-8.009.00/src'
make: *** [modules] B&#322;&#261;d 2

```
 

I think my problem is " RTL8111/8168B PCI Express Gigabit Ethernet controller (**rev 01**)" - old card. Any suggestions?

Again, sorry for my English. I hope you understood my problem.

---

### Post by Fafler on 2010-08-13
You should try contacting the developers. Look for information in the source files. They probably want you to do some regression testing to figure out exactly when the driver stopped working.

Until then, you could try the windows driver with ndiswrapper.

---

### Post by mario64 on 2010-08-13
Thank You for reply.

I send information to the developer.. maybe this help.

Ndiswrapper doesnt work:
```

[   15.357252] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   15.357998] ndiswrapper: driver netrtle (Realtek Semiconductor Corp.,01/22/2009,5.714.0122.2009) loaded
[   15.358907] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 4
[   15.358914] PCI: setting IRQ 4 as level-triggered
[   15.358922] ndiswrapper 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 4 (level, low) -> IRQ 4
[   15.359210] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001388, count: 1, return_address: ffffffffa003681e
[   15.359269] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x605
[   15.359432] ndiswrapper 0000:03:00.0: setting latency timer to 64
[   15.359502] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[   15.359510] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   15.359523] ndiswrapper (mp_halt:262): device ffff88006b3cc680 is not initialized - not halting
[   15.359527] ndiswrapper: device eth%d removed
[   15.359548] ndiswrapper 0000:03:00.0: PCI INT A disabled
[   15.359572] ndiswrapper: probe of 0000:03:00.0 failed with error -22



```

---

### Post by mario64 on 2010-09-07
I solved the problem with wired network. In the newer linux distributions You must disabled PCI-MSI . Add "**pci=nomsi**" to Your grub line and use default kernel module r8169. Tested on ubuntu 10.04 x64.

Greetz, Mariusz Derela

---

### Post by newmatt on 2010-12-07
Can anyone please explain how to go about accomplishing mario64's solution?

---

### Post by mario64 on 2010-12-07
> **newmatt said:**
> Can anyone please explain how to go about accomplishing mario64's solution?
You must edit /etc/default/grub file and add pci=nomsi to option section. After that you must type update-grub2 into terminal. sorry for this short and not completly message but  i type from my mobile :-)

EDIT:
In /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quite splash pci=nomsi"
```

---

