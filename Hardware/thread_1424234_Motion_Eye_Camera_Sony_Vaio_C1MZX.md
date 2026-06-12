---
title: "Motion Eye Camera Sony Vaio C1MZX"
date: 2010-03-07
forum: Hardware
---

### Post by mblanton1234 on 2010-03-07
I am a total newbie to Ubuntu.  I have a Sony Vaio C1MZX and everything is working except the Motion Eye camera.  I have Ubuntu 9.10 Desktop version installed in a dual-boot Ubuntu/Windows XP Pro system. The camera works in Windows. Using Terminal I don't see the camera listed in lsusb or lspci.  Installing the Motioneye software didn't work. Camorama says "no camera found".  Any help is appreciated.

---

### Post by IcarusR on 2010-03-07
I gather sony use a lot of ricoh webcams.
Post output of lsusb.

Long thread about this, might be worth posting there.

[http://ubuntuforums.org/showthread.php?t=968381]("http://ubuntuforums.org/showthread.php?t=968381")

---

### Post by mblanton1234 on 2010-03-07
here is what my lsusb says:

mblanton@mblanton-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 044e:3002 Alps Electric Co., Ltd Bluetooth Device
Bus 001 Device 002: ID 054c:0069 Sony Corp. Memorystick MSC-U03 Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mblanton@mblanton-laptop:~$ 

No mention of a Ricoh camera...I am a total Linux newbie. I followed the link for that driver in the previous post but have no idea how to install it on my system (or even if it is the right driver for my particular laptop).  Any help is greatly appreciated.

---

### Post by mblanton1234 on 2010-03-09
I rebooted under Windows and looked at the camera driver I have installed there.  Apparently it is a PCI driver.  Rebooting under Ubuntu here is the output of the lspci command:

mblanton@mblanton-laptop:~$ lspci
00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
00:00.1 RAM memory: Transmeta Corporation SDRAM controller
00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:0a.0 Multimedia controller: Fujitsu Limited. Device 2011
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Non-VGA unclassified device: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
mblanton@mblanton-laptop:~$ 

I don't recognize any of these as being my webcam, except possibly the Fujitsu device, but I'm not sure.  Any help is greatly appreciated getting my web cam working.

---

