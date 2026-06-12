---
title: "htpc wakes up by itself 3 minutes after suspend"
date: 2010-11-08
forum: Hardware
---

### Post by Nirro on 2010-11-08
Hi all,

I use pm-suspend command to suspend machine, but 3 minutes after suspending, the computer resumes/wakes up by itself.
What's going on ?



# cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P1	  S3	*disabled  
UAR1	  S3	*disabled  pnp:00:03
P0P2	  S3	*disabled  pci:0000:00:1e.0
USB0	  S3	*disabled  pci:0000:00:1d.0
USB1	  S3	*disabled  pci:0000:00:1d.1
USB2	  S3	*disabled  pci:0000:00:1d.2
EUSB	  S3	*disabled  pci:0000:00:1d.7
USB3	  S3	*disabled  pci:0000:00:1a.0
USB4	  S3	*disabled  pci:0000:00:1a.1
USBE	  S3	*disabled  pci:0000:00:1a.7
PEX0	  S4	*disabled  
PEX1	  S4	*disabled  
PEX2	  S4	*disabled  
PEX3	  S4	*disabled  
PEX4	  S4	*disabled  
GBE	  S4	*disabled  pci:0000:00:19.0
USB5	  S3	*disabled  pci:0000:00:1a.2
PWRB	  S5	*disabled  

(Originaly the PWRB was enabled, I disabled it as a test)

# grep . /sys/bus/pci/devices/*/power/wakeup
/sys/bus/pci/devices/0000:00:03.0/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:19.0/power/wakeup:enabled
/sys/bus/pci/devices/0000:00:1a.0/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1a.1/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1a.2/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1a.7/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1b.0/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1d.0/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1d.1/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1d.2/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1d.7/power/wakeup:disabled
/sys/bus/pci/devices/0000:00:1e.0/power/wakeup:disabled
/sys/bus/pci/devices/0000:01:01.0/power/wakeup:disabled

(I tried to change 0000:00:19.0 to disabled, but it changed back)

attachements:
/var/log/pm-suspend.log
dmesg

My motherboard is Intel dg45id + I have a mceusb external IR receiver and an internal imon IR receiver.

Thanks,
Nir.

---

### Post by Nirro on 2010-11-08
Forgot to say that I disabled "Wake On Lan" on BIOS.

Now, I spotted an interesting line in dmesg :

[ 2695.932087] e1000e 0000:00:19.0: **PME# enabled**
[ 2695.932093] e1000e 0000:00:19.0: **wake-up capability enabled by ACPI**

Can the PME# be responsible for the wake ups ?
How do I tell ACPI to not enable this wake-up capability ?

-Nir

---

### Post by Nirro on 2010-11-10
$ uname -a
Linux htpc 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux


Anyone knows ?

---

### Post by Nirro on 2010-11-10
The dmesg messages hint on the ethernet controller :

```
# lspci -vvnns 00:19.0
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
	Subsystem: Intel Corporation Device [8086:5002]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 40
	Region 0: Memory at e0600000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at e0624000 (32-bit, non-prefetchable) [size=4K]
	Region 2: I/O ports at f0e0 [size=32]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 41d1
	Capabilities: [e0] Vendor Specific Information: Len=06 <?>
	Kernel driver in use: e1000e
	Kernel modules: e1000e
```

so I suspected the Wake On Lan again :

```
# ethtool eth0
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
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes


```

I did :
ethtool -s eth0 wol d
and this disabled the wol according to ethtool.
But it didn't work. Still wakes up 3 minutes after suspend.

---

### Post by bvidinli on 2011-01-02
same for me. any clue ?

---

