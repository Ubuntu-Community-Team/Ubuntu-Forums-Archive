---
title: "Transcend TS PDU3 PCIe USB 3.0 expansion card 'Just Works'!"
date: 2012-09-15
forum: Hardware
---

### Post by shreepads on 2012-09-15
Hi

Didn't find mention of this before I bought it, so just wanted to post that this particular PCIe USB3.0 expansion card works just fine on Ubuntu Lucid and Precise 64bit desktops, no tweaks required.

This is a PCIe 2.0 x1 card, details here:
[http://th.transcend-info.com/Products/CatList.asp?LangNo=0&ModNo=283](http://th.transcend-info.com/Products/CatList.asp?LangNo=0&ModNo=283)

Tested speeds using a Transcend Jetflash 700 16GB (USB 3.0) pendrive by copying files > 1GB between /dev/shm and the pendrive (checked swap didn't grow) using rsync (with --stats).

Now my ancient mobo (details below) only has PCIe 1.1 (summary page on ark.intel.com incorrectly states 2.0 support, technical product spec has the right details).

So expected (theoretical) data transfer speed should be the least of:
- PCIe 1.1 x1: 250 MB/s            (PCIe 2.0 x1 is 500 MB/s)
- USB 3.0: 400 MB/s and up        (USB 2.0 is 35 MB/s)
- Transcend Jetflash 700: Read 70 MB/s, Write 20 MB/s

So should mostly be limited to the pendrive capability.

Observed speeds across runs on Lucid and Precise when connected to USB 3.0 slots on the card and USB 2.0 slots on the mobo:

USB 3.0:
- Write: 17 to 25 MB/s (higher end in Precise)
- Read:  66 MB/s

USB 2.0:
- Write: 17 MB/s
- Read:  36 MB/s

lspci details:
```
06:00.0 USB Controller [0c03]: Renesas Technology Corp. Device [1912:0015] (rev 02) (prog-if 30)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e3200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=8
		Vector table: BAR=0 offset=00001000
		PBA: BAR=0 offset=00001080
	Capabilities: [a0] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 unlimited
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [150] #18
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci
```

lsusb details:
```
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-42-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:06:00.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
```

Hmmm for the typical pendrive, if you are focussed on write speed, USB 2.0 will do fine.

---

### Post by shreepads on 2012-09-16
Note that USB drives connected via this card will not be available for selection in the mobo boot setup, i.e. you can't use these for boot drives.

---

### Post by shreepads on 2012-09-30
OK getting 70MB/s and up write speeds on the new WD MyBook 2TB external USB 3.0 drive connected via this card..

So this card is totally worth it!

---

### Post by boshkash1151 on 2013-01-08
I got the PDU3 card 
On ubuntu 12.10 when syncing between two drives formatted as EXT4 i get max speed of 14MB/s

on Windows 7 while syncing between two NTFS drive I get at least 50 MB/s 

Please can anyone help ?

---

### Post by shreepads on 2013-01-22
> **boshkash1151 said:**
> I got the PDU3 card 
On ubuntu 12.10 when syncing between two drives formatted as EXT4 i get max speed of 14MB/s

on Windows 7 while syncing between two NTFS drive I get at least 50 MB/s 

Please can anyone help ?

Are the two drives (ext4/ NTFS) the same make and model? And are the ext4 partitions correctly aligned?

---

### Post by boshkash1151 on 2013-01-30
> **shreepads said:**
> Are the two drives (ext4/ NTFS) the same make and model? And are the ext4 partitions correctly aligned?


the two drives are the same I tested using Ubuntu first while formatted as EXT4 and then I tested the same drives on Windows7 while being formatted as NTFS.

all the EXT4 partitions first sector are 2048 which is equivalent to 1MiB

another thing to note is that when I shared the EXT4 drives using samba, Windows7 can read at a rate of about 50MB/s from those drives and write at about 35MB/s to those drives

---

### Post by streetwriter on 2013-01-31
Didn't work for me. I plugged a SATA power cable into the board, installed the board, turned on the computer, plugged my hard drive into a USB port on the card, and the hard drive doesn't mount.

Am I missing something obvious?

I should add that the hard drive (Seagate 2TB external) is getting power. The blue pilot light is on.

Running 12.04.

Edit: Never mind; now it's working. Guess it took a while to find a driver or something. Showing in Disk Utility with a connection of 705 Mb/s.

---

### Post by streetwriter on 2013-02-01
> **streetwriter said:**
> Showing in Disk Utility with a connection of 705 Mb/s.

Isn't that rather slow for USB 3.0? I was expecting much closer to 5 Gb/s, the max. What factors might be limiting my speed to less than double USB 2.0?

I did a test. 

**Conditions:**

Desktop only. Motherboard supports USB 2.0 and SATA II only
PCIe USB 3.0 expansion card. Powered via SATA cable
External Seagate 2TB Sata III HDD with a USB 3.0 cable
Transferring a 650 MB video file

**Results:**
Internal SSD to attached HD via USB 2.0 @ 480 Mb/s: 21.4 seconds @ 31.2 MB/s
Internal SSD to attached HD via USB 3.0 @ 705 Mb/s: 20 seconds @ 35.2 MB/s

I was careful with capitalisation of Ms above.

It seems I am getting a good transfer speed, no? But the USB 3.0 card isn't doing much for me. Any advice?

---

### Post by boshkash1151 on 2013-02-06
> **boshkash1151 said:**
> I got the PDU3 card 
On ubuntu 12.10 when syncing between two drives formatted as EXT4 i get max speed of 14MB/s

on Windows 7 while syncing between two NTFS drive I get at least 50 MB/s 

Please can anyone help ?


any ideas ?

---

### Post by boshkash1151 on 2013-03-11
in case any one faces the same problem in RSync I specified a temperoray directory that is located on a third drive (not the two syncing) rates now reaches 45MB/s

---

