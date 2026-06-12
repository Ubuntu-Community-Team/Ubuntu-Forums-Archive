---
title: "Ubuntu 5.10 and Asus PVR800-VM"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by ksenos on 2005-12-03
Greetings everyone,

I ve installed ubuntu a few weeks ago but still haven't managed to find a solution to my problems. My motherboard is an ASUS PVR800-VM and is based on the ATI IXP 200 chipset including an onboard VGA chip, ATI RADEON 9100 IGP. To make long story short, here's my lspci output:

```
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5833 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 17)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5834
0000:02:06.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:02:08.0 Ethernet controller: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller (rev 40)
0000:02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)

```

Noticed the Unknown devices? I tried to compile the ATI IXP and ATI RADEON modules within the kernel but still the output is the same. Now, the consequences of the existance of unknown devices seem to be the following:

- The ATI driver is loaded successfully, but each time I wish to run an opengl application the whole system hangs and I must hard reset (this could be due to other issues, as discussed in many other threads).

- The automount is not functioning at all. I also tested the live cd but it is the same there.

- Performance seems not to be optimal. Well, I am not very sure this is because of the missing hardware support, it could be misconfiguration but with other distros (gentoo in particullar) the system seemed to perform better. 

Could someone please help me find a solution? Many thanks :D.

Kostas

---

