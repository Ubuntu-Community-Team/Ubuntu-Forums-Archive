---
title: "Wireless Confuzzlement..."
date: 2010-11-26
forum: Hardware
---

### Post by TenPlus1 on 2010-11-26
This isn't really a complaint but more of a "why does this happen" sorta question...

I have a Compaq M2000 laptop which I installed Ubuntu 10.04 lucid on and everything worked perfectly out of the box, broadcom wireless included...  Then after installing Ubuntu 10.10 maverick the wireless disappered, the wireless on/off button wouldnt work and I couldn't get online without fiddling with ndiswrapper...  Why is this ???

My mother has a Compaq CQ60 laptop which I installed a pre-release of Ubuntu 10.10 RC and everything again worked out of the box, I was so happy that when the final release came out I done a fresh install and again the wireless wasn't working, the wireless on/off button wouldn't work and I couldnt get online, and even ndiswrapper/madwifi wouldn't solve this Atheros nightmare...  Why is this ???

What could be so different from each release (or pre-release) that would cause working wireless drivers not to work ?!?!

---

### Post by carl4926 on 2010-11-26
Never had any trouble like this with my broadcom

```
lspci -nnk
```

will tell us all about your hardware and drivers

---

### Post by TenPlus1 on 2010-11-28
This is what appears:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel modules: snd-intel8x0m
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel modules: i2c-i801
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
06:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Subsystem: Hewlett-Packard Company Compaq nw8240/nx8220 [103c:12f6]
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200
06:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
06:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394
06:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1
06:09.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
	Subsystem: Hewlett-Packard Company Device [103c:3080]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

---

### Post by carl4926 on 2010-11-28
Your device is not broadcom

```
06:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
Subsystem: Hewlett-Packard Company Compaq nw8240/nx8220 [103c:12f6]
Kernel driver in use: ipw2200
Kernel modules: ipw2200
```

---

### Post by TenPlus1 on 2010-11-28
Oops my other laptop is Broadcom, this specific Compaq M2000 is Intel Pro Wireless which SHOULD be supported out of the box with Ubuntu...  10.04 works great, 10.10 doesnt see it at all...

---

### Post by carl4926 on 2010-11-28
It should work and the module looks in place, but

try this:

```
sudo modprobe ipw2200
```
then reboot

---

### Post by TenPlus1 on 2010-11-29
Thanks for the quick reply, I tried that and unfortunately it didn't seem to work, I also tried this to no avail:

sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0 led=1

---

### Post by TenPlus1 on 2010-12-06
Ah hah, I found a fix for my problem on the Compaq M2000 laptop...  Still to test it on the CQ60 though...

In terminal I typed:  more /var/lib/NetworkManager/NetworkManager.state

and this appeared:

[main]
NetworkingEnabled=true
WireleddEnabled=false
WWAEnabled=true

so then I typed:  sudo rfkill unblock all

and from there the wireless light flickered and on reboot it worked perfectly with Ubuntu 10.10 maverick :) woo hoo!

---

