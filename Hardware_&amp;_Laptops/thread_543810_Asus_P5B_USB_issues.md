---
title: "Asus P5B USB issues"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by nandemonai on 2007-09-05
Greetings, 

For a while now I've been meaning to bring this up as I've not found much info on this main board in particular in regard to USB. The JMicron issues with this board seem to be ironed out pretty well in Feisty and for that I am very grateful but I have come across another rather annoying problem: USB.

As far as Keyboards, mice, cams etc go it seems flawless but after recently started using a few pen drives, an IPod and a USB HDD or two I've come across a pretty severe problem.

I've tested all the devices in question on a couple other machines (Windows / Mac) and they seem fine so I'm pretty sure the issue is related to this main board / chipset in particular if not Ubuntu itself. (I'm yet to try another distro for testing as Gutsy Tribe 5 is on my spare partition which also has the same problem unfortunately)

Ok so the problem itself is kind of in two parts:

Firstly, the IPod and pen drives. They mount flawlessly. Plug it in and they show up almost instantly like you would expect. The problem lies in actually trying to use the device. Sometimes it will work fine depending on time frame but eventually, be it 5 mins or 5 hours the device will offline itself and unmount. Usually during a read or write to the device. The Ipod is the worst here, I've not yet managed to get my music library on it completely before it offlines when using either Banshee or GTKPod. (Flat write/reads to the device do the same thing.)

The Pen drives are a little better, they will work most of the time but the longer it is plugged in the more likely it will offline itself. I'm chalking that up to the fact they are much smaller in size and it seems that the larger the copy the more likely the device will offline.

This brings me onto the hard drives I have. I have both a very cheap no name USB to IDE adaptor and a normal all in one Maxtor ext drive.

The no name USB to IDE is a right pain in the butt. It will generally take up to 5-6 attempts at plugging then re-plugging the device into a USB port before it will mount at all. I'm guessing it has something to do with the fact it cost like $20 and I have no idea where it was even made though alas it is flawless in Mac and Windows so again maybe not the device itself. Once it eventually does mount it's the same issue again. Eventually it will offline by itself, more likely during a large read / write.

The Maxtor is essentially the same as the IPod. Mounts fine though the more you use it the more likely it will offline.

I've searched around on both the web and irc but can't seem to find much bar the booting issues for this main board.

Some info:

lspci:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

/var/log/messages after trying to copy my music to the IPod:

```
Sep  6 04:39:43 kurosaki kernel: [ 3291.737556] usb 7-3: new high speed USB device using ehci_hcd and address 6
Sep  6 04:39:43 kurosaki kernel: [ 3291.870472] usb 7-3: configuration #1 chosen from 1 choice
Sep  6 04:39:43 kurosaki kernel: [ 3291.870728] scsi10 : SCSI emulation for USB Mass Storage devices
Sep  6 04:39:48 kurosaki kernel: [ 3296.865152] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Sep  6 04:39:48 kurosaki kernel: [ 3296.866626] SCSI device sdd: 39063023 512-byte hdwr sectors (20000 MB)
Sep  6 04:39:48 kurosaki kernel: [ 3296.867626] sdd: Write Protect is off
Sep  6 04:39:48 kurosaki kernel: [ 3296.869373] SCSI device sdd: 39063023 512-byte hdwr sectors (20000 MB)
Sep  6 04:39:48 kurosaki kernel: [ 3296.870247] sdd: Write Protect is off
Sep  6 04:39:48 kurosaki kernel: [ 3296.870255]  sdd: sdd1 sdd2
Sep  6 04:39:48 kurosaki kernel: [ 3296.938706] sd 10:0:0:0: Attached scsi removable disk sdd
Sep  6 04:39:48 kurosaki kernel: [ 3296.938752] sd 10:0:0:0: Attached scsi generic sg4 type 0
Sep  6 04:44:55 kurosaki kernel: [ 3603.313115] sdd: Current: sense key: No Sense
Sep  6 04:44:55 kurosaki kernel: [ 3603.313121]     Additional sense: No additional sense information
Sep  6 04:44:55 kurosaki kernel: [ 3603.313127] Info fld=0x0
Sep  6 04:44:59 kurosaki kernel: [ 3607.107478] sdd: Current: sense key: No Sense
Sep  6 04:44:59 kurosaki kernel: [ 3607.107485]     Additional sense: No additional sense information
Sep  6 04:44:59 kurosaki kernel: [ 3607.107491] Info fld=0x0
Sep  6 04:45:05 kurosaki kernel: [ 3613.476743] sdd: Current: sense key: No Sense
Sep  6 04:45:05 kurosaki kernel: [ 3613.476750]     Additional sense: No additional sense information
Sep  6 04:45:05 kurosaki kernel: [ 3613.476756] Info fld=0x0
Sep  6 04:45:08 kurosaki kernel: [ 3615.995707] sdd: Current: sense key: No Sense
Sep  6 04:45:08 kurosaki kernel: [ 3615.995724]     Additional sense: No additional sense information
Sep  6 04:45:08 kurosaki kernel: [ 3615.995730] Info fld=0x0
Sep  6 04:45:23 kurosaki kernel: [ 3631.379159] sdd: Current: sense key: No Sense
Sep  6 04:45:23 kurosaki kernel: [ 3631.379165]     Additional sense: No additional sense information
Sep  6 04:45:23 kurosaki kernel: [ 3631.379172] Info fld=0x0
Sep  6 04:45:27 kurosaki kernel: [ 3635.642188] sdd: Current: sense key: No Sense
Sep  6 04:45:29 kurosaki kernel: [ 3635.642194]     Additional sense: No additional sense information
Sep  6 04:45:29 kurosaki kernel: [ 3635.642200] Info fld=0x0
Sep  6 04:45:39 kurosaki kernel: [ 3647.662737] sdd: Current: sense key: No Sense
Sep  6 04:45:41 kurosaki kernel: [ 3647.662743]     Additional sense: No additional sense information
Sep  6 04:45:41 kurosaki kernel: [ 3647.662749] Info fld=0x0
Sep  6 04:45:41 kurosaki kernel: [ 3648.748248] sdd: Current: sense key: No Sense
Sep  6 04:45:41 kurosaki kernel: [ 3648.748254]     Additional sense: No additional sense information
Sep  6 04:45:41 kurosaki kernel: [ 3648.748260] Info fld=0x0
Sep  6 04:45:48 kurosaki kernel: [ 3655.982549] sdd: Current: sense key: No Sense
Sep  6 04:45:48 kurosaki kernel: [ 3655.982554]     Additional sense: No additional sense information
Sep  6 04:45:48 kurosaki kernel: [ 3655.982560] Info fld=0x0
Sep  6 04:45:50 kurosaki kernel: [ 3657.921866] sdd: Current: sense key: No Sense
Sep  6 04:45:50 kurosaki kernel: [ 3657.921873]     Additional sense: No additional sense information
Sep  6 04:45:50 kurosaki kernel: [ 3657.921879] Info fld=0x0
Sep  6 04:45:57 kurosaki kernel: [ 3665.294743] sdd: Current: sense key: No Sense
Sep  6 04:45:57 kurosaki kernel: [ 3665.294749]     Additional sense: No additional sense information
Sep  6 04:45:57 kurosaki kernel: [ 3665.294756] Info fld=0x0
Sep  6 04:45:57 kurosaki kernel: [ 3665.424957] sdd: Current: sense key: No Sense
Sep  6 04:45:57 kurosaki kernel: [ 3665.424963]     Additional sense: No additional sense information
Sep  6 04:45:57 kurosaki kernel: [ 3665.424969] Info fld=0x0
Sep  6 04:46:02 kurosaki kernel: [ 3669.745785] sdd: Current: sense key: No Sense
Sep  6 04:46:07 kurosaki kernel: [ 3669.745792]     Additional sense: No additional sense information
Sep  6 04:46:07 kurosaki kernel: [ 3669.745798] Info fld=0x0
Sep  6 04:46:07 kurosaki kernel: [ 3671.768873] sdd: Current: sense key: No Sense
Sep  6 04:46:07 kurosaki kernel: [ 3671.768879]     Additional sense: No additional sense information
Sep  6 04:46:07 kurosaki kernel: [ 3671.768885] Info fld=0x0
Sep  6 04:46:10 kurosaki kernel: [ 3677.692941] sdd: Current: sense key: No Sense
Sep  6 04:46:10 kurosaki kernel: [ 3677.692947]     Additional sense: No additional sense information
Sep  6 04:46:10 kurosaki kernel: [ 3677.692954] Info fld=0x0
Sep  6 04:46:10 kurosaki kernel: [ 3678.274962] sdd: Current: sense key: No Sense
Sep  6 04:46:10 kurosaki kernel: [ 3678.274968]     Additional sense: No additional sense information
Sep  6 04:46:10 kurosaki kernel: [ 3678.274974] Info fld=0x0
Sep  6 04:46:14 kurosaki kernel: [ 3682.510656] sdd: Current: sense key: No Sense
Sep  6 04:46:16 kurosaki kernel: [ 3682.510661]     Additional sense: No additional sense information
Sep  6 04:46:16 kurosaki kernel: [ 3682.510666] Info fld=0x0
Sep  6 04:46:17 kurosaki kernel: [ 3685.136110] sdd: Current: sense key: No Sense
Sep  6 04:46:17 kurosaki kernel: [ 3685.136116]     Additional sense: No additional sense information
Sep  6 04:46:17 kurosaki kernel: [ 3685.136123] Info fld=0x0
Sep  6 04:46:20 kurosaki kernel: [ 3688.363932] sdd: Current: sense key: No Sense
Sep  6 04:46:21 kurosaki kernel: [ 3688.363937]     Additional sense: No additional sense information
Sep  6 04:46:21 kurosaki kernel: [ 3688.363944] Info fld=0x0
Sep  6 04:46:24 kurosaki kernel: [ 3692.157923] sdd: Current: sense key: No Sense
Sep  6 04:46:25 kurosaki kernel: [ 3692.157929]     Additional sense: No additional sense information
Sep  6 04:46:25 kurosaki kernel: [ 3692.157935] Info fld=0x0
Sep  6 04:46:25 kurosaki kernel: [ 3693.378270] sdd: Current: sense key: No Sense
Sep  6 04:46:25 kurosaki kernel: [ 3693.378276]     Additional sense: No additional sense information
Sep  6 04:46:25 kurosaki kernel: [ 3693.378282] Info fld=0x0
Sep  6 04:46:27 kurosaki kernel: [ 3694.972773] sdd: Current: sense key: No Sense
Sep  6 04:46:30 kurosaki kernel: [ 3694.972779]     Additional sense: No additional sense information
Sep  6 04:46:30 kurosaki kernel: [ 3694.972785] Info fld=0x0
Sep  6 04:46:30 kurosaki kernel: [ 3695.423327] sdd: Current: sense key: No Sense
Sep  6 04:46:30 kurosaki kernel: [ 3695.423332]     Additional sense: No additional sense information
Sep  6 04:46:30 kurosaki kernel: [ 3695.423337] Info fld=0x0
Sep  6 04:46:30 kurosaki kernel: [ 3697.660522] sdd: Current: sense key: No Sense
Sep  6 04:46:30 kurosaki kernel: [ 3697.660527]     Additional sense: No additional sense information
Sep  6 04:46:30 kurosaki kernel: [ 3697.660532] Info fld=0x0
Sep  6 04:46:30 kurosaki kernel: [ 3698.188233] sdd: Current: sense key: No Sense
Sep  6 04:46:30 kurosaki kernel: [ 3698.188238]     Additional sense: No additional sense information
Sep  6 04:46:30 kurosaki kernel: [ 3698.188243] Info fld=0x0
Sep  6 04:46:45 kurosaki kernel: [ 3712.824255] sdd: Current: sense key: No Sense
Sep  6 04:46:45 kurosaki kernel: [ 3712.824260]     Additional sense: No additional sense information
Sep  6 04:46:45 kurosaki kernel: [ 3712.824266] Info fld=0x0
Sep  6 04:46:46 kurosaki kernel: [ 3714.197405] sdd: Current: sense key: No Sense
Sep  6 04:46:47 kurosaki kernel: [ 3714.197411]     Additional sense: No additional sense information
Sep  6 04:46:47 kurosaki kernel: [ 3714.197416] Info fld=0x0
Sep  6 04:46:48 kurosaki kernel: [ 3715.591030] sdd: Current: sense key: No Sense
Sep  6 04:46:48 kurosaki kernel: [ 3715.591036]     Additional sense: No additional sense information
Sep  6 04:46:48 kurosaki kernel: [ 3715.591041] Info fld=0x0
Sep  6 04:46:49 kurosaki kernel: [ 3717.166057] sdd: Current: sense key: No Sense
Sep  6 04:46:49 kurosaki kernel: [ 3717.166063]     Additional sense: No additional sense information
Sep  6 04:46:49 kurosaki kernel: [ 3717.166068] Info fld=0x0
Sep  6 04:46:54 kurosaki kernel: [ 3722.377892] sdd: Current: sense key: No Sense
Sep  6 04:46:55 kurosaki kernel: [ 3722.377898]     Additional sense: No additional sense information
Sep  6 04:46:55 kurosaki kernel: [ 3722.377903] Info fld=0x0
Sep  6 04:47:17 kurosaki kernel: [ 3745.447580] sdd: Current: sense key: No Sense
Sep  6 04:47:17 kurosaki kernel: [ 3745.447586]     Additional sense: No additional sense information
Sep  6 04:47:17 kurosaki kernel: [ 3745.447591] Info fld=0x0
Sep  6 04:47:19 kurosaki kernel: [ 3747.142579] sdd: Current: sense key: No Sense
Sep  6 04:47:19 kurosaki kernel: [ 3747.142584]     Additional sense: No additional sense information
Sep  6 04:47:19 kurosaki kernel: [ 3747.142589] Info fld=0x0
Sep  6 04:47:20 kurosaki kernel: [ 3747.999754] sdd: Current: sense key: No Sense
Sep  6 04:47:20 kurosaki kernel: [ 3747.999760]     Additional sense: No additional sense information
Sep  6 04:47:20 kurosaki kernel: [ 3747.999765] Info fld=0x0
Sep  6 04:47:51 kurosaki kernel: [ 3779.282281] usb 7-3: reset high speed USB device using ehci_hcd and address 6
Sep  6 04:48:02 kurosaki kernel: [ 3789.513104] usb 7-3: reset high speed USB device using ehci_hcd and address 6
Sep  6 04:48:18 kurosaki kernel: [ 3805.840096] usb 7-3: reset high speed USB device using ehci_hcd and address 6
Sep  6 04:48:18 kurosaki kernel: [ 3806.087781] usb 7-3: reset high speed USB device using ehci_hcd and address 6
Sep  6 04:48:28 kurosaki kernel: [ 3816.320173] usb 7-3: reset high speed USB device using ehci_hcd and address 6
Sep  6 04:48:29 kurosaki kernel: [ 3816.453072] sd 10:0:0:0: scsi: Device offlined - not ready after error recovery
Sep  6 04:48:29 kurosaki kernel: [ 3816.453083] sd 10:0:0:0: SCSI error: return code = 0x00050000
Sep  6 04:48:29 kurosaki kernel: [ 3816.453086] end_request: I/O error, dev sdd, sector 6961885
Sep  6 04:48:29 kurosaki kernel: [ 3816.456479] printk: 11947 messages suppressed.
Sep  6 04:48:29 kurosaki kernel: [ 3816.456485] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456492] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456497] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456503] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456508] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456513] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456519] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456524] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456531] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.456537] lost page write due to I/O error on sdd2
Sep  6 04:48:29 kurosaki kernel: [ 3816.457117] sd 10:0:0:0: SCSI error: return code = 0x00010000
Sep  6 04:48:29 kurosaki kernel: [ 3816.457119] end_request: I/O error, dev sdd, sector 6914149
```

uname -a:

```
Linux kurosaki 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
```

If anyone has any ideas on what's going on or can point me to a fix I'd be most grateful.

---

### Post by amias on 2007-09-05
have you tried using various combinations and documenting the stability ? it maybe that a rogue device is messing it up for the others . 

Toodle-pip
Amias

---

### Post by nandemonai on 2007-09-05
> **amias said:**
> have you tried using various combinations and documenting the stability ? it maybe that a rogue device is messing it up for the others . 

Toodle-pip
Amias

"I've tested all the devices in question on a couple other machines (Windows / Mac) and they seem fine so I'm pretty sure the issue is related to this main board / chipset in particular if not Ubuntu itself. (I'm yet to try another distro for testing as Gutsy Tribe 5 is on my spare partition which also has the same problem unfortunately)"

Because of the issues I've been trying device by device. I never have anything other than said device and a keyboard / mouse attached via USB.

This post pretty much sums up my experiences with only one device attached at a time.

I could post the messages I get when other devices offline (not just the ipod) but the messages are identical as with the ipod so I don't really see much point unfortunately.

---

### Post by smorar on 2007-09-09
I can confirm that I have the exact same issue with my Ipod and USB, and I am struggling to find any other information out there on it.

My current system is Feisty, (freshly installed):
```

Linux shadow 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

```

I get the following output in /var/log/messages:
```

Sep  9 20:05:54 shadow kernel: [27378.807501] Info fld=0x0
Sep  9 20:05:57 shadow kernel: [27381.453440] sdb: Current: sense key: No Sense
Sep  9 20:05:57 shadow kernel: [27381.453446]     Additional sense: No additional sense information
Sep  9 20:05:57 shadow kernel: [27381.453450] Info fld=0x0
Sep  9 20:06:00 shadow kernel: [27385.062515] sd 8:0:0:0: SCSI error: return code = 0x10070000
Sep  9 20:06:01 shadow kernel: [27385.062520] end_request: I/O error, dev sdb, sector 31365635

```
This issue has been occurring on this machine since edgy (i think), and it was fine on much older ubuntu distributions.
This doesn't occur on my other Ubuntu Feisty machines, nor using Firewire.
My motherboard is a MSI K8 Neo Platinum (I think)

---

