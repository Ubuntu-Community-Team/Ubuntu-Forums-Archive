---
title: "linksys ADSL2MUE usb modem help setup please"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by Choad on 2005-11-24
i have a linksys adsl2mue modem connected via usb to my computer. it is the "always on" type

on installation (of ubuntu), it said it had detected a firewire ethernet connection, and that it could use that as its ethernet connection, but that it was unlikely to be correct. i chose to ignore it. is that likely to have been my modem detected? if so how do i re detect it?

i am a quasi linux newbie and a total ubuntu/gnome newbie, so i really need the help of you kind forum people :D

thanks

---

### Post by Lambert on 2005-11-24
It's probably detected as that just identifies all the attached devices. It may not have a driver for it though.

Go to terminal and type this  command

sudo lshw -businfo

Look for the device in this list and notice what the class is. Then

sudo lshw -C <class>

where class = the devices' class from the first command

Post that output here along with the output of the command lsusb

---

### Post by Choad on 2005-11-24
> 
richard@ubuntu:~$ **sudo lshw -businfo**
Password:
Bus info     Device    Class          Description
=================================================
                       system         Desktop Computer
                       bus            SiS-730
                       memory         BIOS
cpu@0                  processor      AMD Athlon(tm) XP 1700+
                       memory         L1 cache
                       memory         L1 cache
                       memory         L2 cache
                       memory         L2 cache
                       memory         Flash Memory
                       memory         DIMM
                       memory         DIMM
                       memory         DIMM [empty]
pci@00:00.0            bridge         730 Host
pci@00:00.1            storage        5513 [IDE]
ide@0        ide0      bus            IDE Channel 0
ide@0.0      /dev/hda  disk           WDC WD400EB-11CPF0
ide@0.1      /dev/hdb  disk           ExcelStor Technology J880
ide@1        ide1      bus            IDE Channel 1
ide@1.1      /dev/hdd  disk           _NEC DVD_RW ND-3520A
pci@00:01.0            bridge         SiS85C503/5513 (LPC Bridge)
pci@00:01.2            bus            USB 1.0 Controller
usb@1        usb1      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller
pci@00:01.3            bus            USB 1.0 Controller
usb@2        usb2      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
**usb@2:1                communication  Linksys RNDIS Network Adapter**
pci@00:02.0            bridge         Virtual PCI-to-PCI bridge (AGP)
pci@01:00.0            display        Radeon RV200 QW [Radeon 7500]
pci@00:09.0            multimedia     SB Live! EMU10k1
pci@00:09.1            input          SB Live! MIDI/Game Port
pci@00:0d.0            network        Marvell W8300 802.11 Adapter
richard@ubuntu:~$ **sudo lshw -C communication**
  *-usb UNCLAIMED
       description: Communication device
       product: Linksys RNDIS Network Adapter
       vendor: Texas Instruments
       physical id: 1
       bus info: usb@2:1
       version: 0.00
       capabilities: usb-1.10
       configuration: maxpower=0mA speed=12.0MB/s
richard@ubuntu:~$ **lsusb**
Bus 002 Device 002: ID 13b1:000f
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
richard@ubuntu:~$


as requested :)

(ahhh i hate the way forums dont keep spaces. it looks messy. hope you can extract the info)

---

### Post by Choad on 2005-11-25
ermmm. sorry to bump but i would like to get on the interweb with ubuntu :)

---

### Post by Choad on 2005-11-26
bump

---

