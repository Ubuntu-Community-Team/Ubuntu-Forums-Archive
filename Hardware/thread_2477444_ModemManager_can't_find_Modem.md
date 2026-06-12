---
title: "ModemManager can't find Modem?"
date: 2022-07-25
forum: Hardware
---

### Post by raffaeledp on 2022-07-25
[COLOR=#232629][FONT=-apple-system]I've two modem connected to my device. When I scan for modems and show them, I can find only one of them. This is a brief report: (I'm on Ubuntu 18.04 LTS, 5.04 kernel)[/FONT][/COLOR]
```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]admin@sintrones-abox:~$ lsusb[/FONT][/COLOR]
Bus 002 Device 002: ID 1e0e:901e Qualcomm / Option
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04d8:0205 Microchip Technology, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
admin@sintrones-abox:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 9b43 (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 9bc5 (rev 05)
00:12.0 Signal processing controller: Intel Corporation Device 06f9
00:14.0 USB controller: Intel Corporation Device 06ed
00:14.2 RAM memory: Intel Corporation Device 06ef
00:14.5 SD Host controller: Intel Corporation Device 06f5
00:16.0 Communication controller: Intel Corporation Device 06e0
00:16.3 Serial controller: Intel Corporation Device 06e3
00:17.0 SATA controller: Intel Corporation Device 06d2
00:1b.0 PCI bridge: Intel Corporation Device 06ac (rev f0)
00:1b.5 PCI bridge: Intel Corporation Device 06ad (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device 06bd (rev f0)
00:1c.6 PCI bridge: Intel Corporation Device 06be (rev f0)
00:1c.7 PCI bridge: Intel Corporation Device 06bf (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device 06b0 (rev f0)
00:1d.1 PCI bridge: Intel Corporation Device 06b1 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 06b6 (rev f0)
00:1d.7 PCI bridge: Intel Corporation Device 06b7 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0687
00:1f.3 Audio device: Intel Corporation Device 06c8
00:1f.4 SMBus: Intel Corporation Device 06a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 06a4
00:1f.6 Ethernet controller: Intel Corporation Device 0d4c
01:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
02:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
03:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
04:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
05:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
06:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
07:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
08:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
09:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
admin@sintrones-abox:~$ sudo mmcli -L
[sudo] password for admin: [COLOR=var(--black-800)][FONT=var(--ff-mono)]    /org/freedesktop/ModemManager1/Modem/0 [QCOM] SDXPRAIRIE-MTP _SN:1E3B9ABB[/FONT][/COLOR]
```
[COLOR=#232629][FONT=-apple-system]I really don't know where the problem is...anyway, I found something strange writing systemctl status ModemManager:[/FONT][/COLOR]
```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]admin@sintrones-abox:~$ systemctl status ModemManager[/FONT][/COLOR]
&#9679; ModemManager.service - Modem Manager
   Loaded: loaded (/lib/systemd/system/ModemManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2022-07-25 07:52:08 UTC; 58min ago
 Main PID: 1622 (ModemManager)
    Tasks: 5 (limit: 4915)
   CGroup: /system.slice/ModemManager.service
           &#9500;&#9472;1622 /usr/sbin/ModemManager --filter-policy=strict
           &#9492;&#9472;2078 /usr/lib/libmbim/mbim-proxy

Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:13:43 sintrones-abox ModemManager[1622]: <info>  Couldn't check support for device '/sys/devices/p
Jul 25 08:14:06 sintrones-abox ModemManager[1622]: <info>  [device /sys/devices/pci0000:00/0000:00:14.0/usb1
Jul 25 08:14:06 sintrones-abox ModemManager[1622]: <warn>  Could not grab port (tty/ttyACM0): 'Cannot add po [COLOR=var(--black-800)][FONT=var(--ff-mono)]Jul 25 08:14:06 sintrones-abox ModemManager[1622]: <warn>  Couldn't create modem for device '/sys/devices/pc[/FONT][/COLOR]
```
[COLOR=#232629][FONT=-apple-system]As you can see there are two types of warnings...[/FONT][/COLOR]
```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]<warn>  Could not grab port (tty/ttyACM0): 'Cannot add po[/FONT][/COLOR]
[COLOR=var(--black-800)][FONT=var(--ff-mono)]    Jul 25 08:14:06 sintrones-abox ModemManager[1622]: <warn>  Couldn't create modem for device '/sys/devices/pc[/FONT][/COLOR]
```
[COLOR=#232629][FONT=-apple-system][FONT=inherit]How can I try to solve them?[/FONT]


[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Autodave on 2022-07-25
Is this a laptop or desktop?  How are the modems connected?

I gotta ask.....why 2?

---

