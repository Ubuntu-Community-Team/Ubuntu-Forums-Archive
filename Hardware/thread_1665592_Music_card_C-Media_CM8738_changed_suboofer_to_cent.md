---
title: "Music card C-Media CM8738 changed suboofer to central speaker."
date: 2011-01-12
forum: Hardware
---

### Post by lesniak on 2011-01-12
I have music card: C-Media CM8738 and Creative 5.1 speakers. When I'm testing my speakers in audio control my suboofer is playing sound which my central speaker should play and my central speaker play sound which my suboofer should play. Any ideas?

Sorry for my english :P

aplay -l:
> lesniak@pinkdesktop:~$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: ICH5 [Intel ICH5], urz&#261;dzenie 0: Intel ICH [Intel ICH5]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: ICH5 [Intel ICH5], urz&#261;dzenie 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 2: CMI8738 [C-Media CMI8738], urz&#261;dzenie 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 2: CMI8738 [C-Media CMI8738], urz&#261;dzenie 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Urz&#261;dzenia podrz&#281;dne: 0/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 2: CMI8738 [C-Media CMI8738], urz&#261;dzenie 2: CMI8738-MC6 [C-Media PCI IEC958]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0


and lspci:
> lesniak@pinkdesktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


---

