---
title: "PCMCIA (CardBus) USB hub"
date: 2016-12-04
forum: Hardware
---

### Post by professorhughes on 2016-12-04
Hi,

I am having trouble getting either of two PCMCIA Cardbus USB hubs to work. The one I am having the most success with has three ports (the other has four) and I'm getting the following output from terminal:
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV250/M9 GL [Mobility FireGL 9000/Radeon 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
03:00.0 Unassigned class [ffff]: NEC Corporation OHCI USB Controller (rev 43)
03:00.1 USB controller: NEC Corporation OHCI USB Controller (rev 43)
03:00.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)

```

I read on another [forum]("http://www.pclinuxos.com/forum/index.php?topic=94725.0") that in troubleshooting it is useful to:

[LIST=1]
[*]Unplug the card.
[*]Run this command: service syslog start
[*]Run this command: echo "" > /var/log/syslog
[*]plug back in the card and then wait for around five seconds
[*]Run this command and give your output: cat /var/log/syslog
[/LIST]
When this was done this was the output:
```
root@ubuntu:/home/nigel# service syslog start
root@ubuntu:/home/nigel# echo "" > /var/log/syslog
root@ubuntu:/home/nigel# cat /var/log/syslog
root@ubuntu:/home/nigel# dmesg | tail -n 20
[  821.612265] ohci-pci 0000:03:00.0: init 0000:03:00.0 fail, -16
[  821.612274] ohci-pci: probe of 0000:03:00.0 failed with error -16
[  821.612332] pci 0000:03:00.1: enabling device (0000 -> 0002)
[  821.612781] ohci-pci 0000:03:00.1: OHCI PCI host controller
[  821.612791] ohci-pci 0000:03:00.1: new USB bus registered, assigned bus number 5
[  823.180890] ohci-pci 0000:03:00.1: irq 11, io mem 0x4c001000
[  823.181195] ohci-pci 0000:03:00.1: HC died; cleaning up
[  823.236760] ohci-pci 0000:03:00.1: USB HC reset timed out!
[  823.236773] ohci-pci 0000:03:00.1: can't start
[  823.236822] ohci-pci 0000:03:00.1: startup error -1
[  823.236834] ohci-pci 0000:03:00.1: USB bus 5 deregistered
[  823.237025] ohci-pci 0000:03:00.1: init 0000:03:00.1 fail, -1
[  823.237036] ohci-pci: probe of 0000:03:00.1 failed with error -1
[  823.237100] pci 0000:03:00.2: enabling device (0000 -> 0002)
[  823.237227] pci 0000:03:00.2: EHCI: unrecognized capability 00
[  823.237531] ehci-pci 0000:03:00.2: EHCI Host Controller
[  823.237543] ehci-pci 0000:03:00.2: new USB bus registered, assigned bus number 5
[  823.237603] ehci-pci 0000:03:00.2: can't setup: -19
[  823.237608] ehci-pci 0000:03:00.2: USB bus 5 deregistered
[  823.237712] ehci-pci 0000:03:00.2: init 0000:03:00.2 fail, -19

```

Could I please have some help in understanding what is the next step in getting the USB hub to work?
Thanks heaps,
Nigel.

ps. The version of the Linux kernel installed is 4.4.0-47-generic

---

### Post by professorhughes on 2016-12-06
I found that in an old record about the compatibility of laptops with Ubuntu that there was some mention about interrupt conflicts with the Dell Latitude D600 I have that could be resolved by disabling the parallel port. Hence I disabled the parallel port in the BIOS and now the PCMCIA card works!

---

