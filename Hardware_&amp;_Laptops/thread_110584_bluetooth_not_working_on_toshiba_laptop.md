---
title: "bluetooth not working on toshiba laptop"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by zasf on 2005-12-31
Hi all,

I'm trying to get the internal bluetooth device working on my Toshiba laptop. I already installed the (I hope) needed packages.

I leave you the following commands that might help

```
matteo@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5653
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:06:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:06.4 0805: Texas Instruments: Unknown device 8034
```
```
matteo@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 0000:0000
```
```
matteo@ubuntu:~$ lsmod | grep bluetooth
bluetooth              43012  6 hci_usb,hidp,rfcomm,l2cap
```
```
matteo@ubuntu:~$ hcitool dev
Devices:
```

The point is that, using this [hotwo]("http://www.ubuntuforums.org/showthread.php?t=34740&highlight=Bluetooth+gps"), I was able to use my father's USB bluetooth dongle but not the internal I have on the laptop. How can I know if the sistem recognized my internal device? What's the address for it?

Thank you.

---

### Post by zasf on 2006-01-05
Bluetooth internal device was disabled by the window partition (even if the on/off button on the laptop was turned on).

If you encounter the same problem, my advice is to boot up win (I know you have it on your system, do cheat :) ) and turn it on with the specific hotkey.

Matteo

---

### Post by luistorresmx on 2007-10-23
I can't get my bluetooth working on my Compaq TC4200. I figured that this could be the solution, but I have major problem, I have no windows partition and I did turned off bluetooth when I had Windows.

All I have is Windows Emulated by VirtualBox.But I understand that emulators work only with devices already discovered by Ubuntu.

So, do I have to reinstall Windows to solve this? There should be another way to do this with linux, if Windows was capable of turning off bluetooth Linux should be too!! This is a MAJOR problem for users like me, that are switching completely to Ubuntu.

Any Idea????

By the way, tried every other solution I found here, so right now I am desesperated...:confused:

---

### Post by luistorresmx on 2007-10-23
Is there a way to run HP Wireless Assistant on Ubuntu? Maybe using WINE??

 I tried by myself, however, I get an error when a DLL calls HPQNT.hpqIsHpFamily

Ideas?

---

