---
title: "HP ZV5340US  cardbus not issues..."
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by jiovine on 2005-11-14
Oddly enough, most everything has gone smooth except for the expected Broadcom wireless issues...so I purchased a edimax wifi pc card but have discovered my cardbus is not recognized...can someone point me in the right direction?

Running Breezy 32Bit: Here is the output from lspci:

jiovine@Ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[COLOR="Red"]0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
0000:02:04.2 System peripheral: Texas Instruments: Unknown device 8201 (rev 01)[/COLOR]

Any help is appreciated...

-John

---

### Post by nocturn on 2005-11-15
Maybe this helps:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard?highlight=%28laptop%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard?highlight=%28laptop%29)

Note: Try for zv5000's PCMCIA in /etc/pcmcia/config.opts lines 'include port 0x3000-0x7fff' and 'memory 0xe8100000-0xe97fffff' (reboot required).

---

### Post by jiovine on 2005-11-15
[QUOTE=nocturn]Maybe this helps:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard?highlight=%28laptop%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard?highlight=%28laptop%29)

Note: Try for zv5000's PCMCIA in /etc/pcmcia/config.opts lines 'include port 0x3000-0x7fff' and 'memory 0xe8100000-0xe97fffff' (reboot required).[/QUOTE]

Forgive me for being such a newbie...

I opened the config.opts file, added the lines.  Upon save it will not allow me to save the file to that directory...

What am I doing wrong or how do I log in as root?

---

### Post by jiovine on 2005-11-15
[QUOTE=jiovine]Forgive me for being such a newbie...

I opened the config.opts file, added the lines.  Upon save it will not allow me to save the file to that directory...

What am I doing wrong or how do I log in as root?[/QUOTE]

Well figured out how to edit with the sudo gedit...

but made the adjustments and Cardbus is still unknow device status... :(

---

