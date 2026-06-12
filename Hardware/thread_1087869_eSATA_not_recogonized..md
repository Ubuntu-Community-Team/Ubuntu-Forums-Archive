---
title: "eSATA not recogonized."
date: 2009-03-05
forum: Hardware
---

### Post by NobleSavage on 2009-03-05
I'm using Hardy

I added an eSATA controller to a pci slot in my computer and plugged in an external drive.

I don't see the drive showing up

blkid :

> /dev/sda1: TYPE="swap" UUID="b76692f1-2197-4c04-873f-1c63133eba9c" 
/dev/sda2: UUID="415ba131-dee4-43af-ab53-39194749043d" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="2c840450-084f-17b8-43c6-9c06105f034f" 
/dev/sdb6: UUID="eb2f2e4a-db21-4536-b5bd-e48c2ce37d72" SEC_TYPE="ext2" TYPE="ext3" 
 


sda & sdb are internal drives.  


lspci:

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 USB Controller: OPTi Inc. 82C861 (rev 10)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



Any ideas or suggestions???

---

### Post by Therion on 2009-03-05
Can you find the newly installed SATA controller-card in your system's BIOS?

---

### Post by NobleSavage on 2009-03-05
Hey Therion,

Not sure.  I just poked around the BIOS setup.  It's not listed in the boot order screen.   Other than that, I'm not sure what to look for.

The motherboard and BIOS are older (it doesn't even have onboard sata) so this might be the problem.  

I tried downloading the BIOS update and it's a windows only .exe.  :(

This might be the excuse I need to upgrade my computer. :P

---

### Post by Therion on 2009-03-05
> **NobleSavage said:**
> Hey Therion,

Not sure.  I just poked around the BIOS setup.  It's not listed in the boot order screen.   Other than that, I'm not sure what to look for.
Hey yourself, studmuffin.

Well this is a PCI card, correct, with SATA ports on the back?  Since it's a PCI card, it should be listed in the **PCI/PnP Configuration** section of your BIOS.

You may have to poke around in some of the other areas like... Advanced Chipset Features or Onboard Devices or some such.  Can't tell you exactly where it would be found but if the card is not being picked up by your BIOS, you're dead in the water.  If it is, and your 'buntu no find it, you *could* be looking at a hardware incompatibility issue.  

But "Don't Panic" just yet...  Save your panic.  Poke now, panic later.

---

### Post by partsdale on 2009-03-05
"Poke now, panic later."


that's just funny

---

### Post by jylppy on 2009-05-23
I had a same problem on ASUS M3A78-EMH HDMI motherboard. Once I changed the SATA setting in BIOS to ACHI it started to recognize the hotplugged drives. So please try that. 

I do not know any nice way to unplug so I just umount filesystems and switch of the power from eSATA enclosure. It gives some nasty kernel messages but it seems to be otherwise OK... Some guru, could help here.

---

