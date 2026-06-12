---
title: "How/where to find drivers for a laptop"
date: 2011-09-07
forum: Hardware
---

### Post by graphicsRat on 2011-09-07
I've just installed 64-bit Ubuntu on a customized Novatech NSPIRE 2410 laptop and evereything works fine, except that I don't have any drivers installed. I've run

```
lspci -nn
```

Output:
```
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
04:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
05:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
```

Now I'd like to know how and where to get drivers for these components.

Thanks.

Edit: additional info from the utility Hardinfo
Processors
Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz 	2601.00MHz
Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz 	2601.00MHz
Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz 	800.00MHz
Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz 	800.00MHz

Memory
Total Memory 	8105012 kB
Free Memory 	6975484 kB
Buffers 	143856 kB
Cached 	416220 kB
Cached Swap 	0 kB
Active 	579080 kB
Inactive 	248596 kB
Active(anon) 	267888 kB
Inactive(anon) 	4876 kB
Active(file) 	311192 kB
Inactive(file) 	243720 kB
Unevictable 	0 kB
Mlocked 	0 kB
Virtual Memory 	15624184 kB
Free Virtual Memory 	15624184 kB
Dirty 	32 kB
Writeback 	0 kB
AnonPages 	267860 kB
Mapped 	71260 kB
Shmem 	5160 kB
Slab 	79236 kB
SReclaimable 	58700 kB
SUnreclaim 	20536 kB
KernelStack 	2272 kB
PageTables 	19140 kB
NFS_Unstable 	0 kB
Bounce 	0 kB
WritebackTmp 	0 kB
CommitLimit 	19676688 kB
Committed_AS 	778376 kB
VmallocTotal 	34359738367 kB
VmallocUsed 	119984 kB
VmallocChunk 	34359614444 kB
HardwareCorrupted 	0 kB
HugePages_Total 	0
HugePages_Free 	0
HugePages_Rsvd 	0
HugePages_Surp 	0
Hugepagesize 	2048 kB
DirectMap4k 	10228 kB
DirectMap2M 	8294400 kB

PCI Devices
Host bridge 	Intel Corporation Device 0104 (rev 09)
PCI bridge 	Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
VGA compatible controller 	Intel Corporation Device 0126 (rev 09)
Communication controller 	Intel Corporation Cougar Point HECI Controller #1 (rev 04)
USB Controller 	Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05) (prog-if 20)
Audio device 	Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
PCI bridge 	Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
PCI bridge 	Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
PCI bridge 	Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
PCI bridge 	Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
USB Controller 	Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05) (prog-if 20)
ISA bridge 	Intel Corporation Device 1c49 (rev 05)
SATA controller 	Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05) (prog-if 01)
SMBus 	Intel Corporation Cougar Point SMBus Controller (rev 05)
VGA compatible controller 	nVidia Corporation Device 0df4 (rev a1)
Network controller 	Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
USB Controller 	NEC Corporation Device 0194 (rev 04) (prog-if 30)
Ethernet controller 	Atheros Communications Device 1083 (rev c0)

---

### Post by Beacon11 on 2011-09-07
> **graphicsRat said:**
> I've just installed 64-bit Ubuntu on a customized Novatech NSPIRE 2410 laptop and evereything works fine, except that I don't have any drivers installed.

I mean no offense by this, but are you new to Linux? It sounds like you're expecting a Windows-like process of hunting for chipset drivers, networking drivers, video drivers, etc. In most cases, you don't have to do that in Ubuntu. Is something behaving as it shouldn't that would imply that you need drivers installed?

---

### Post by coffeecat on 2011-09-07
> **graphicsRat said:**
>  evereything works fine, except that I don't have any drivers installed.

Well - if everything is working fine then you must have drivers installed. Yes?

Expecting to have to install drivers is a Windows thing - I agree with Beacon11. I've had a look through your lspci output and everything there should work just fine. The drivers come with a default install. The only thing you may wish to install a different driver for is the nvidia graphics. It'll give you a perfectly good display with the default nouveau driver, but if you want 3d acceleration (for compiz, for example) then you'll want to install the proprietary "nvidia" driver. Open the app variously named Additional Drivers or Hardware Drivers depending on the Ubuntu release you are running (you don't say which) and that will recommend and install the proprietary driver for you.

---

### Post by Beacon11 on 2011-09-07
> **coffeecat said:**
> The only thing you may wish to install a different driver for is the nvidia graphics.

Agreed. This isn't installed by default giving you the option of choosing a FOSS driver or a proprietary one. As Coffeecat pointed out, there are numerous advantages to the proprietary one, and I recommend it.

---

