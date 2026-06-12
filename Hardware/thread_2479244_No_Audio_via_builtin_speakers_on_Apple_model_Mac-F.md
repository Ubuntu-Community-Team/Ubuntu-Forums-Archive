---
title: "No Audio via builtin speakers on Apple model: Mac-FFE5EF870D7BA81A  (v: iMac16,2)"
date: 2022-09-19
forum: Hardware
---

### Post by vevak on 2022-09-19
Hello Ubuntu community,

I am new to Ubuntu.

Help will be much appreciated regarding sound output via builtin speakers for iMac16,2

Everything works except the sound output via builtin speakers. 

I do not own / have a set of 3.5mm headphone to check the sound via headphone jack on iMac 16,2

only available headphones I have are with a lighting connector that will likely to require buying a dongle :(

Bluetooth headphone work & so does the iMac (16,2) keyboard

only issue with iMac (16,2) keyboard is when dual booting to macOS Bluetooth keyboard has to be re-paired in Ubuntu 

Some of the answers in the forum suggested using commands below to help isolate problem

I have tired my ´newbie´ level best to collect info and if some kind soul can help fix this problem

I have used Zorin distro (16.1) and sound via builtin speakers worked when ´output devices´ set to ´speaker-builtin audio' and configuration set to ´analogue surround 2.1 output´

This does not seem to fix the issue using Ubuntu 22.04.1

To my newbie experience, I suppose there is likely a bug in Ubuntu 22.04.1 as Zorin distro itself is based on Ubuntu

Many thanks in advnace


---------------------------------------------------------------


$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xb1710000 irq 61
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xb1714000 irq 62


---------------------------------------------------------------                    
                     
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: CS4208 Analog [CS4208 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: CS4208 Digital [CS4208 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---------------------------------------------------------------


$ sudo inxi -SMA
System:
  Host: *********-**** Kernel: 5.15.0-47-generic x86_64 bits: 64
    Console: pty pts/1 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: Apple product: iMac16,2 v: 1.0 serial: ***********
  Mobo: Apple model: Mac-FFE5EF870D7BA81A v: iMac16,2
    serial: ************   UEFI: Apple v: 430.140.3.0.0 date: 04/18/2022
Audio:
  Device-1: Intel Broadwell-U Audio driver: snd_hda_intel
  Device-2: Intel 9 Series Family HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-47-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes


---------------------------------------------------------------
$ uname -ro
5.15.0-47-generic GNU/Linux
---------------------------------------------------------------


$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge - DMI (rev 0a)
00:01.0 PCI bridge: Intel Corporation Broadwell-U PCI Express x16 Controller (rev 0a)
00:01.1 PCI bridge: Intel Corporation Broadwell-U PCI Express x8 Controller (rev 0a)
00:02.0 VGA compatible controller: Intel Corporation Iris Pro Graphics 6200 (rev 0a)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 0a)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1f.0 ISA bridge: Intel Corporation HM97 Chipset LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
00:1f.6 Signal processing controller: Intel Corporation 9 Series Chipset Family Thermal Controller
01:00.0 Mass storage controller: Apple Inc. S1X NVMe Controller (rev 01)
03:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC (rev 01)
04:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe (rev 01)
04:00.1 SD Host controller: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader (rev 01)
05:00.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:00.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:03.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:04.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:05.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:06.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
07:00.0 System peripheral: Intel Corporation DSL5520 Thunderbolt 2 NHI [Falcon Ridge 4C 2013]
---------------------------------------------------------------

---

