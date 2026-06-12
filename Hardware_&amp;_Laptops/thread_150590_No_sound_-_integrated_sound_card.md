---
title: "No sound - integrated sound card"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by Patrol on 2006-03-26
Hi all !
I got a new computer recently. My sound card is integrated on my mother board ( ASUS P5LD2 ). But ... I've got no sound !

*aplay -l* gives
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


*lspci* gives
> 0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770 (rev 02)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771 (rev 02)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corp.: Unknown device 27d6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)
0000:04:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0091 (rev a1)


I've checked up my system : sound is not muted ^^....

Maybe the cause is my kernel version : 2.6.12-9-386... ( I use Kubuntu ).

I've never got this problem before so I don't know what to do...

I installed *alsa-driver* but it doesn't change anything ...

Thanks to help me.

---

### Post by Patrol on 2006-03-27
up :rolleyes:

---

