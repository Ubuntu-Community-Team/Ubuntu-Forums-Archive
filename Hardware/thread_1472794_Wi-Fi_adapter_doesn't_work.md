---
title: "Wi-Fi adapter doesn't work"
date: 2010-05-04
forum: Hardware
---

### Post by alexem8 on 2010-05-04
Hi,

I have PCI Wi-Fi adapter Netgear WPN311. It worked fine out of box in Ubuntu 9.10, but not in 10.04
```
iwconfig:
lo        no wireless extensions.
eth0      no  wireless extensions.

lspci -vv
00:0a.0 Ethernet controller: Atheros Communications Inc. Device f716  (rev 01)
   Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV-  VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status: Cap+  66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort-  <MAbort- >SERR- <PERR+ INTx-
   Latency: 32, Cache Line  Size: 32 bytes
   Interrupt: pin A routed to IRQ 5
   Region 0:  Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
   Capabilities:  <access denied>

00:12.0 Ethernet controller: VIA  Technologies, Inc. VT6102 [Rhine-II] (rev 78)
   Subsystem: ASUSTeK  Computer Inc. Device 80ff
   Control: I/O+ Mem+ BusMaster+ SpecCycle-  MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status:  Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort-  <MAbort- >SERR- <PERR- INTx-
   Latency: 32 (750ns min,  2000ns max), Cache Line Size: 32 bytes
   Interrupt: pin A routed to  IRQ 23
   Region 0: I/O ports at e800 [size=256]
   Region 1:  Memory at 80000100 (32-bit, non-prefetchable) [size=256]
   Capabilities:  <access denied>
   Kernel driver in use: via-rhine
   Kernel  modules: via-rhine

```
So NetworkManager has only Wired network: ath0

After installing Madwifi **lspci -vv** has some changes:
```
00:0a.0 Ethernet controller: Atheros Communications Inc. Atheros  AR5001X+ Wireless Network Adapter (rev 01)
   Subsystem: Netgear  Device 5600
   Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV-  VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status: Cap+  66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort-  <MAbort- >SERR- <PERR+ INTx-
   Interrupt: pin A routed to  IRQ 18
   Region 0: Memory at d0000000 (32-bit, non-prefetchable)  [size=64K]
   Capabilities: <access denied>
**   Kernel  modules: ath_pci, ath5k**

00:12.0 Ethernet controller: VIA  Technologies, Inc. VT6102 [Rhine-II] (rev 78)
   Subsystem: ASUSTeK  Computer Inc. Device 80ff
   Control: I/O+ Mem+ BusMaster+ SpecCycle-  MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status:  Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort-  <MAbort- >SERR- <PERR- INTx-
   Latency: 32 (750ns min,  2000ns max), Cache Line Size: 32 bytes
   Interrupt: pin A routed to  IRQ 23
   Region 0: I/O ports at e400 [size=256]
   Region 1:  Memory at 80000100 (32-bit, non-prefetchable) [size=256]
   Capabilities:  <access denied>
   Kernel driver in use: via-rhine
   Kernel  modules: via-rhine
```
But still nothing changed in the system.
Swopped modules using **modprobe -r**, blacklisted them **/etc/modprobe.d/blacklist-ath_pci.conf**. Also changed **/etc/modules** one by one. Rebooted every time. BUT NOTHING! :(

---

### Post by alexem8 on 2010-05-04
any ideas???

---

### Post by alexem8 on 2010-05-05
Is this the RIGHT place for questions???

---

### Post by Wheel_nut on 2010-05-05
I am not a techie but I believe that the default Wireless Driver was changed between 9.10 and 10.04. 

On 9.10 and prior releases, my 3COM 3CRWE154G72 PC Card worked  but my MSI Ralink Card didn't. On 10.04, the Ralink Card works but the 3Com doesn't.

I hope this gives you a clue to a solution. In my scant experience, Wireless Drivers are a minefield and although I got a lot of help from Forum contributors, I wasn't able to crack the problem.

---

### Post by alexem8 on 2010-05-05
Thank you.
I think it is not only driver problem, but kernel.
I tried different proprietary drivers without any success.

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be  helping for other Netgear adapters. Or  You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :smile:

---

### Post by StGermain on 2010-05-09
I had the same problem going from 9.10 to 10.04

As my internal broadcom card on my Dell D410 is crap I was using a pcmcia 3Com card which was working perfectly untill the update.

I have been able to make it work by doing a sudo apt-get install linux-firmware-nonfree however that lead to total lockups so I had to remove it again.

I have now switched the card for one with an Atheros chipset and that seems to be working fine...

I have been on Ubuntu since 7.04 and it's things like this that make it hard to recommend it to non-tech users which is really unfortunate.

---

### Post by bigtel on 2010-11-04
I have just updated to 10.04 and I have the same problem with my 3Com card. 

Has anyone come up with any sort of solution for this?

---

