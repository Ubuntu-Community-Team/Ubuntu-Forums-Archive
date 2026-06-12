---
title: "Sony Vaio vgn-fz21e webcam not found"
date: 2011-06-12
forum: Hardware
---

### Post by derekreilly on 2011-06-12
Hi,

I am running Ubuntu 11.04 on a Sony Vaio vgn-fz21e laptop. I want to use Skype for video calls but the webcam is not found.

Saying that, without doing anything, suddenly it worked last night but today again it is not found.

I have opened cheese webcam booth and get message: no device found.

I have looked all over the place and found no solution. It still baffles me how it worked last night.

Any ideas how to get this working?

Derek.

---

### Post by trozamon on 2011-06-12
Open up a terminal and try running this command:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

---

### Post by derekreilly on 2011-06-13
Hi,

I receive the below message, Skype opens but still no webcam found.

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by trozamon on 2011-06-13
Are you running 32bit? If you are, run this command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```That might work if you are on 32-bit.
If that doesn't work, paste the output from the following commands:

```
lsusb
ls /dev/ | grep video
lspci
```

---

### Post by derekreilly on 2011-06-13
> **trozamon said:**
> Are you running 32bit? If you are, run this command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```That might work if you are on 32-bit.
If that doesn't work, paste the output from the following commands:

```
lsusb
ls /dev/ | grep video
lspci
```

32 bit, yes


I tried LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
It opened Skype without any message in the trminal but still no webcam.

Output from ```
lsusb
ls /dev/ | grep video
lspci
```[/QUOTE] is below:


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0d8c:0126 C-Media Electronics, Inc. 
Bus 005 Device 004: ID 045e:00d2 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bb4:0ff9 High Tech Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by trozamon on 2011-06-13
Did you run all three commands? I don't see any output from "ls /dev/ | grep video" or "lspci". Just run the command "ls /dev/ | grep video" and post the output - no need to run "lspci" since we already know your webcam is connected.

Anyways, your webcam is listed in the output from "lsusb". Open up synaptic package manager and seach for "libv4l". If it isn't installed, install it. If it is installed already, search for and install "v4l-utils". Run this is a terminal:

```
v4l2-compliance
```

and post that output. There's a lot of info here; if you need an explanation, just ask.

---

### Post by derekreilly on 2011-06-13
derek@CM1031722-B:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0d8c:0126 C-Media Electronics, Inc. 
Bus 005 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0df6:003f Sitecom Europe B.V. WL-608 Wireless USB Adapter 54g
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
derek@CM1031722-B:~$ ls /dev/ | grep video
derek@CM1031722-B:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GT] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Synaptic package manager is installed, "libv4l" and "v4l-utils" already installed.

I ran v4l2-compliance in a terminal and received this:
v4l2-compliance: command not found

---

### Post by derekreilly on 2011-06-13
I got it to work by following the instruction on this page:[http://ubuntuforums.org/showthread.php?t=1597534](http://ubuntuforums.org/showthread.php?t=1597534)

I found that by googling "Camera VGP-VCC8" which I notice in the results from the terminal.

Thanks Trozamol, you may not have came up with the solution but you pointed me in the right direction! :)

Thanks again!

Derek.

---

