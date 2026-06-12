---
title: "[SOLVED] Sd card not showing up in /dev/"
date: 2008-11-11
forum: General Help
---

### Post by James- on 2008-11-11
I have a Richo card reader(Dell XPS M170) although the SD card auto-mounts when inserted I cannot find it in /dev/ folder (gparted cant either) I right clicked>properties and doesn't give me the address to /dev/ folder

Essentially I need this to reformat the card(I know how)

lspci:
> 
james@james-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7800 GTX] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)


lsusb

> 
james@james-laptop:~$ lsusb
Bus 005 Device 002: ID 04fc:0c25 Sunplus Technology Co., Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 004 Device 002: ID 046d:c048 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by Queue29 on 2008-11-11
/media

---

### Post by James- on 2008-11-12
i can't do :sudo mkdosfs -F 32 /media/NIKON\ D80/

---

### Post by philinux on 2008-11-12
Not done this for a while. I think you need to use fdisk on the card first to delete any partitions and create a new fat32 one.

[http://www.oreillynet.com/linux/cmd/cmd.csp?path=f/fdisk](http://www.oreillynet.com/linux/cmd/cmd.csp?path=f/fdisk)

---

### Post by James- on 2008-11-12
*sigh* the problem is to do mkdosfs or fdisk I NEED THE SD CARD TO SHOW UP IN /DEV/ WHICH IT IS **NOT**

every thing that says [device]...guess where it has to be.../dev/....


EDIT:

never mind found it:
> 
mount


lists all devices that are currently mounted with their /dev/ location

> 
/dev/mmcblk0p1 on /media/NIKON D80 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


---

