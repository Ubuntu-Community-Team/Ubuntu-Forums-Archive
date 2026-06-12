---
title: "Wireless function key Acer Aspire 5742ZG"
date: 2011-01-29
forum: Hardware
---

### Post by kr0n1x on 2011-01-29
Hi, I've got this notebook: Acer Aspire 5742ZG

Short hardware description:
Intel Pentium P6100
ATI Mobility Radeon HD 5470
4 GB DDR3 Ram
320 GB HDD

lspci output:
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

I've found many threads that talk about the function keys working in bad ways, and I've found some "half" solutions (many were for Acer Aspire One netbooks). The problem is that many similar notebooks (with similar 5742 code) have very different hardware, so I decided to open a new thread (also because I'm posting accurate logs, I hope it will help you solving my problem).

I'm experiencing some problems using Function keys on my laptop (I'm talking about the blue printed keys, e.g. Fn+F3 key combination disables my wireless card, Fn+F7 disables my touchpad, etc.).

The worst combination at the moment is Fn+F3, the one which should disable my wireless card.
Checking a log (thanks System Log Viewer) I've noticed that I've to press it 3 (three) times to disable my wireless card.
And if I want to enable it again? Well I have to press it 2 times.

Here's the log: [http://pastebin.com/rBS31H9U](http://pastebin.com/rBS31H9U)
I've replaced my router mac address with: 00:11:00:11:00:11
and my wireless card mac address with the opposite (11:00:11:00:11:00).
(is it generally safe to post mac addresses? xD I wasn't sure so...)

Is there a way to fix this problem?

The test has been made with Ubuntu 10.10 32bit (from an USB stick, thanks to universal usb installer).
I've had the same problem with the 64bit version, but I've tried if pressing the combination more than 1 time could work.

Thanks for the support, tell me if you need more info (and how to get that info, possibly).

Bye

---

### Post by kr0n1x on 2011-01-30
Test has been made also with Ubuntu 10.10 64bit now, same problem.

Any help?

---

### Post by kr0n1x on 2011-02-01
I've installed and updated Ubuntu 10.10 64bit and the problem is still present.
Any way to fix it? Anyway now I've got more brightness levels.

---

