---
title: "No Sound in Karmic x86_64 with creative x-fi"
date: 2009-12-07
forum: Hardware
---

### Post by Deadlyhydra on 2009-12-07
I have just installed Karmic 64bit on my pc, I have a Creative X-fi pci sound card in my system as well as an onboard audio card, wich is disabled in the BIOS, and i can't seem to get the audio working at all. I am a total n00b at linux. However reading from other posts the outcome of sudo lspci is the following: 
deadlyhydra@ubuntu:~$ sudo lspci
[sudo] password for deadlyhydra: 
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0a.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
00:0b.0 Multimedia audio controller: Creative Labs SB X-Fi
00:0c.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600GT] (rev a1)

I also tried othe OS's like windows and Kubuntu and the sound workes fine through the card. In Kubuntu it actually works out of the box, but wanted to try ubuntu as the KDE desktop was annoying me. Any ideas?

---

