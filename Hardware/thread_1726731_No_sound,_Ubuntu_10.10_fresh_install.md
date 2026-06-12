---
title: "No sound, Ubuntu 10.10 fresh install"
date: 2011-04-11
forum: Hardware
---

### Post by a392 on 2011-04-11
Hi all,I am trying to convert the family over to Ubuntu and different computers are having different issues but i will post their issues seperately. We have an older computer that we havent used because it is too slow, installed Ubuntu 10.04 and is it so much faster now. However, no sound(it was working with windows vista). I upgraded to 10.10 and it worked for the other computers but not one. I have been looking at many tutorials here but nothing is working. Here is some specs. Any advice is greatly appreciated. Thanks

code:sudo lshw -c sound

*-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:41 memory:ffa34000-ffa37fff




code:cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xffa34000 irq 41




code:cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.



code: uname -a
Linux p5c2r-RP831AV-ABA-s7700y 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux



code:aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




code: lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:01.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 02)

---

### Post by sakishrist on 2011-04-11
Hi,

Try with headphones, if it's working with them then try: System -> Preferences -> Sound -> Output (tab) -> Connector and select Analog Speakers

---

