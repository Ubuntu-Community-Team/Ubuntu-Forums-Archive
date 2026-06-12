---
title: "Sound Problem!!! CA0106"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by calin_ionut on 2007-04-20
Hi everyone! I have a big problem with the sound. I have a ga-g1975x motherboard, and my sound card is SB live! 24 bit and it`s onboard. I just downloaded and install the new distribution  Ubuntu 7.04 - the Feisty Fawn. It`s :lolflag:  but my sound dont work :confused:  
Here i have some information: 

calin@DarkStar:~$ lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
04:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:06.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (ASUS 8211 (ITE IT8212 ATA RAID Controller)) (rev 11)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)



calin@DarkStar:~$ /usr/sbin/hwinfo --sound
25: PCI 405.0: 0401 Multimedia audio controller
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1102_7
  Unique ID: wJko.TWUl3XHi5+9
  Parent ID: 6NW+.clCealCK_QA
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:04:05.0
  SysFS BusID: 0000:04:05.0
  Hardware Class: sound
  Model: "Giga-byte SB Audigy LS"
  Vendor: pci 0x1102 "Creative Labs"
  Device: pci 0x0007 "SB Audigy LS"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xa006
  Driver: "CA0106"
  Driver Modules: "snd_ca0106"
  I/O Ports: 0x9000-0xafff (rw)
  IRQ: 22 (16160 events)
  Module Alias: "pci:v00001102d00000007sv00001458sd0000A006bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_ca0106 is active
    Driver Activation Cmd: "modprobe snd_ca0106"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)


calin@DarkStar:~$ modinfo soundcore
filename:       /lib/modules/2.6.20-15-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     45750F13477CBA5B6F36F46
depends:
vermagic:       2.6.20-15-generic SMP mod_unload 586


Any sugestions? please help!!!!

---

### Post by nanooklabs on 2007-05-21
I Have exactly same problem. Looks like everything is ok but there is no sound.

---

### Post by AKA3Toes on 2007-07-21
> **calin_ionut said:**
> [size=1][i]Hi everyone! I have a big problem with the sound. I have a ga-g1975x motherboard, and my sound card is SB live! 24 bit and it`s onboard. I just downloaded and install the new distribution  Ubuntu 7.04 - the Feisty Fawn. It`s :lolflag:  but my sound dont work :confused:  
Here i have some information: 

calin@DarkStar:~$ lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
04:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:06.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (ASUS 8211 (ITE IT8212 ATA RAID Controller)) (rev 11)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)



calin@DarkStar:~$ /usr/sbin/hwinfo --sound
25: PCI 405.0: 0401 Multimedia audio controller
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1102_7
  Unique ID: wJko.TWUl3XHi5+9
  Parent ID: 6NW+.clCealCK_QA
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:04:05.0
  SysFS BusID: 0000:04:05.0
  Hardware Class: sound
  Model: "Giga-byte SB Audigy LS"
  Vendor: pci 0x1102 "Creative Labs"
  Device: pci 0x0007 "SB Audigy LS"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xa006
  Driver: "CA0106"
  Driver Modules: "snd_ca0106"
  I/O Ports: 0x9000-0xafff (rw)
  IRQ: 22 (16160 events)
  Module Alias: "pci:v00001102d00000007sv00001458sd0000A006bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_ca0106 is active
    Driver Activation Cmd: "modprobe snd_ca0106"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)


calin@DarkStar:~$ modinfo soundcore
filename:       /lib/modules/2.6.20-15-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     45750F13477CBA5B6F36F46
depends:
[color=darkred]vermagic:       2.6.20-15-generic SMP mod_unload 586[/color]


Any sugestions? please help!!!![/size][/font][FONT="Times New Roman"][size=2][color=darkred]---If you haven't found a solution yet, you might try [[color=deepskyblue]_Audigy LS for Linux at Creative's site_[/color]]("http://us.creative.com/support/downloads/") (you'll probably have to go through the drop down box applet yourself), rather than just accepting the generic drivers. 

---Browsing Gigabyte's suport section on their website first (In hope of helping you with your problem, I was looking for a copy of an users' manual to see if maybe yours has a jumper [JBIO on mine... IIRC] like my MSI K8N for "front/rear audio ports"), I found this in bright, pretty red text under the download section:[indent]Gigabyte @ [[color=deepskyblue]_ Their website _[/color]](http://www.giga-byte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1955&ProductName=GA-G1975X)says, [size=1][color=red][/i]1. Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset
vendors' website or 3rd party website.[/size][i][/color][/indent]

---GL![/color][/font][/size][/i]

---

### Post by toey on 2007-08-24
The solution to this bug is here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2801](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2801), comment 0014189.

I have successfully gotten sound working on my g1975x running debain 2.6.21-2-amd64 following the linked post... good luck ;)

---

