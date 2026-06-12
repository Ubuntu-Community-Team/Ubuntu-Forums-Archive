---
title: "Two Kworld DVB Tuners - One wont tune!"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by mike-g on 2007-08-06
Hi,

I have been using a KWorld DVBT-100 digittal TV tuner on ubuntu no problems - I got a second one the other day so I could record 2 programmes at once. Whats weird is either tuner works when plugged in individually - the are PCI devices -  but when both are plugged in one wont tune . although the tuning programmes in Kaffeine and Myth both run showing both cards - but never actually lock on.

My guess is there is some  clash between the two cards because they are the same?

I have tried messing with BIOS PCI interrupts but to no effect.

Any way the lspci :

00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:00.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:02.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:02.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)


Anyone with any ideas? Thanks!!

---

