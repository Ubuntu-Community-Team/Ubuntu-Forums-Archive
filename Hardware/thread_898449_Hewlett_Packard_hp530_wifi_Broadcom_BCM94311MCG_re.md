---
title: "Hewlett Packard hp530 wifi Broadcom BCM94311MCG rev 01"
date: 2008-08-23
forum: Hardware
---

### Post by anti_user on 2008-08-23
Hello! I have this laptop and this wifi. WiFi doesnt work, im trying all variants and nothing works... Please type only workings variants for THIS card. My info:>
```
lspci -vv
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 1364
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 <4us, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Kernel driver in use: b43-pci-bridge

uname -a

Linux inithp 2.6.26.3 #2 Sat Aug 23 19:43:44 YEKST 2008 i686 Intel(R) Celeron(R) M CPU        440  @ 1.86GHz GenuineIntel GNU/Linux

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg

b43-phy0: Broadcom 4311 WLAN found
Broadcom 43xx driver loaded [ Features: P, Firmware-ID: FW13 ]

dmesg after ifconfig wlan0 up

firmware: requesting b43/ucode5.fw
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).

(but there already yet this firmware)


```

Anybody from this forum make this card to work. Type here please howto only for card this revision

---

### Post by sergiom99 on 2008-08-23
I got mine working with the spript and how to that Dark_stang posted here:
[http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

Mine is a BCM4328, but his card is a BCM4311.

---

