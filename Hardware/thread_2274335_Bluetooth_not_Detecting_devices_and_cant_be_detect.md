---
title: "Bluetooth not Detecting devices and cant be detected"
date: 2015-04-19
forum: Hardware
---

### Post by martin154 on 2015-04-19
Hi Community,

I have just got a new laptop HP15 and have been having some problems with Linux Mint, so have now made the jump to Ubuntu. The overall gui experience is much smoother than with mint, however I have come across a snag and need your help. I have searched the www but cant find a solution.

My internal bluetooth device is detected with hci, the icon is in the taskbar, but when scanning for bluetooth devices it finds nothing and it itself cannot be found. I have installed blueman and rebooted, there is neither a hardware nor software block in place. I really dont know where to go troubleshooting this.

Thanks in advance for your tips.

Regards
Martin

---

### Post by jeremy31 on 2015-04-19
Please post ```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```

And I will see what can or can't be done

---

### Post by martin154 on 2015-04-19
> **jeremy31 said:**
> Please post ```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```

And I will see what can or can't be done

here you are:
jones@jones-hp:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux jones-hp 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:2230]
    Kernel driver in use: wl
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:22cd]
    Kernel driver in use: r8169
Bus 002 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:216c Broadcom Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   14.632378] Bluetooth: Core ver 2.19
[   14.632408] Bluetooth: HCI device and connection manager initialized
[   14.632420] Bluetooth: HCI socket layer initialized
[   14.632424] Bluetooth: L2CAP socket layer initialized
[   14.632442] Bluetooth: SCO socket layer initialized
[   14.678562] bluetooth hci0: Direct firmware load failed with error -2
[   14.678568] bluetooth hci0: Falling back to user helper
[   14.679856] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-0a5c-216c.hcd not found
[   16.676528] Bluetooth: RFCOMM TTY layer initialized
[   16.676544] Bluetooth: RFCOMM socket layer initialized
[   16.676555] Bluetooth: RFCOMM ver 1.11
[   16.682600] Bluetooth: hci0 command 0x1003 tx timeout
[   16.724877] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.724883] Bluetooth: BNEP filters: protocol multicast
[   16.724895] Bluetooth: BNEP socket layer initialized
[    0.319219] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.389387] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.390115] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.604851] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.649688] [Firmware Bug]: battery: (dis)charge rate invalid.
[   12.146781] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   13.197284] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[   14.678562] bluetooth hci0: Direct firmware load failed with error -2
bluetooth             446409  22 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth

---

### Post by jeremy31 on 2015-04-19
OK, an easy one
```
wget https://www.dropbox.com/s/r6q9zt59darq80n/BCM43142A0-0a5c-216c.hcd
```
```
sudo cp BCM43142A0-0a5c-216c.hcd /lib/firmware/brcm/BCM43142A0-0a5c-216c.hcd
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```

And it should work

---

### Post by martin154 on 2015-04-19
> **jeremy31 said:**
> OK, an easy one
```
wget https://www.dropbox.com/s/r6q9zt59darq80n/BCM43142A0-0a5c-216c.hcd
```
```
sudo cp BCM43142A0-0a5c-216c.hcd /lib/firmware/brcm/BCM43142A0-0a5c-216c.hcd
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```

And it should work

it is working! Many thanks for the fast and effective support.

Looks like ill be staying with UBUNTU!

---

### Post by martin154 on 2015-04-24
sorry to "unsolve" this thread but I have now come across another BT hitch. Tried to connect the laptop via bluetooth to my audio unit but it only connects very shortly then disconnects again. this BT unit is my stereo unit which should act as BT speakers.
Any ideas?

---

### Post by bach on 2015-04-24
I am having the same problem with Ubuntu 15.04 on a DELL XPS 13 (model 9343) notebook. I am attaching some info. Suggestions are welcome. 

cribari@darwin4:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux darwin4 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell Device [1028:0019]
	Kernel driver in use: wl
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0c45:670c Microdia 
Bus 001 Device 004: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 002: ID 046d:c530 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.136553] Bluetooth: Core ver 2.20
[    2.136568] Bluetooth: HCI device and connection manager initialized
[    2.136572] Bluetooth: HCI socket layer initialized
[    2.136575] Bluetooth: L2CAP socket layer initialized
[    2.136581] Bluetooth: SCO socket layer initialized
[    2.138896] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    2.138899] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[    3.407444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.407448] Bluetooth: BNEP filters: protocol multicast
[    3.407452] Bluetooth: BNEP socket layer initialized
[    3.413492] Bluetooth: RFCOMM TTY layer initialized
[    3.413499] Bluetooth: RFCOMM socket layer initialized
[    3.413504] Bluetooth: RFCOMM ver 1.11
[    2.138896] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
bluetooth             491520  22 bnep,btusb,rfcomm
cribari@darwin4:~$

---

### Post by jeremy31 on 2015-04-24
> **martin154 said:**
> sorry to "unsolve" this thread but I have now come across another BT hitch. Tried to connect the laptop via bluetooth to my audio unit but it only connects very shortly then disconnects again. this BT unit is my stereo unit which should act as BT speakers.
Any ideas?

Audio over bluetooth can be a pain.  Sometimes it can be fixed with ```
sudo pactl load-module module-bluetooth-discover
``` and then pair with the audio.  If you are using blueman, it will unload the module every boot.

---

### Post by jeremy31 on 2015-04-24
> **bach said:**
> I am having the same problem with Ubuntu 15.04 on a DELL XPS 13 (model 9343) notebook. I am attaching some info. Suggestions are welcome. 

cribari@darwin4:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux darwin4 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Kernel driver in use: wl
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0c45:670c Microdia 
Bus 001 Device 004: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 002: ID 046d:c530 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.136553] Bluetooth: Core ver 2.20
[    2.136568] Bluetooth: HCI device and connection manager initialized
[    2.136572] Bluetooth: HCI socket layer initialized
[    2.136575] Bluetooth: L2CAP socket layer initialized
[    2.136581] Bluetooth: SCO socket layer initialized
[    2.138896] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    2.138899] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[    3.407444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.407448] Bluetooth: BNEP filters: protocol multicast
[    3.407452] Bluetooth: BNEP socket layer initialized
[    3.413492] Bluetooth: RFCOMM TTY layer initialized
[    3.413499] Bluetooth: RFCOMM socket layer initialized
[    3.413504] Bluetooth: RFCOMM ver 1.11
[    2.138896] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
bluetooth             491520  22 bnep,btusb,rfcomm
cribari@darwin4:~$

I answered your question [http://askubuntu.com/questions/613614/bluetooth-not-working-in-ubuntu-15-04](http://askubuntu.com/questions/613614/bluetooth-not-working-in-ubuntu-15-04)

---

### Post by Pilot6 on 2015-04-25
Jeremy31,

Maybe it is time to make a ppa with all Broadcom firmware? It will make things easier for everyone.

---

### Post by jeremy31 on 2015-04-25
> **Pilot6 said:**
> Jeremy31,

Maybe it is time to make a ppa with all Broadcom firmware? It will make things easier for everyone.

Is it legal?  I figured if it was legal Ubuntu would have included it in linux-firmware by now.

Issue #2 is that I am not sure where the changing point was for the naming structure, in some kernels it wants /lib/firmware/fw-VID_PID.hcd and other kernels want /lib/firmware/brcm/BCM*****-VID-PID.hcd

---

### Post by giosimar on 2015-04-25
The solution given was useful also for me!

Thank you very much!

---

### Post by Pilot6 on 2015-04-26
> **jeremy31 said:**
> Is it legal?  I figured if it was legal Ubuntu would have included it in linux-firmware by now.

Issue #2 is that I am not sure where the changing point was for the naming structure, in some kernels it wants /lib/firmware/fw-VID_PID.hcd and other kernels want /lib/firmware/brcm/BCM*****-VID-PID.hcd

1. No, it is not quite legal. Broadcom did not gave right to distribution. But placing it in Dropbox is not legal either. ;) But I do not think that it was done with intension not to let using it in Linux. I can pot it in my repo. I doubt Broadcom will sue me.

2. PPA's are specific for Ubuntu distro. As far as I noticed for kernels up to 3.19 VID-PID will work, it can be checked.

---

### Post by SA6 on 2015-04-27
I followed the instructions in post #5, except for replacing the VID and PID with mine, and this is what I got: 

> modprobe btusb
Can't get device info: No such device
modprobe: ERROR: ../libkmod/libkmod-module.c:959 command_do() Error running install command for btusb
modprobe: ERROR: could not insert 'btusb': Operation not permitted



Any suggestions? 

Thanks in advance.

PS:

> Linux sa6-Z510 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
	Kernel driver in use: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo Device [17aa:0611]
	Kernel driver in use: wl
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 105b:e065  
Bus 003 Device 004: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 003: ID 1915:7777 Nordic Semiconductor ASA 
Bus 003 Device 010: ID 045e:02ae Microsoft Corp. Xbox NUI Camera
Bus 003 Device 008: ID 045e:02b0 Microsoft Corp. Xbox NUI Motor
Bus 003 Device 009: ID 045e:02ad Microsoft Corp. Xbox NUI Audio
Bus 003 Device 007: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 006: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 002: ID 5986:029d Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    3.430390] Bluetooth: Core ver 2.19
[    3.430402] Bluetooth: HCI device and connection manager initialized
[    3.430409] Bluetooth: HCI socket layer initialized
[    3.430410] Bluetooth: L2CAP socket layer initialized
[    3.430416] Bluetooth: SCO socket layer initialized
[    4.469201] Bluetooth: RFCOMM TTY layer initialized
[    4.469211] Bluetooth: RFCOMM socket layer initialized
[    4.469221] Bluetooth: RFCOMM ver 1.11
[    4.587054] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.587057] Bluetooth: BNEP filters: protocol multicast
[    4.587065] Bluetooth: BNEP socket layer initialized
[    0.200817] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.413636] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x595f03)
[    3.788417] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
bluetooth             446409  11 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth


---

### Post by Pilot6 on 2015-04-27
SA6,

Your adapter [COLOR=#000000][I]105b:e065
[/I][/COLOR]is not supported by the kernel yet. It is
 LenovoChina 43228+20702 combo

---

### Post by jeremy31 on 2015-04-27
SA6

```
wget https://www.dropbox.com/s/0rmgeve2ibrh1u1/bluetooth-3.16-2.tar.gz
```
```
wget https://www.dropbox.com/s/f503f6r686riiow/fw-105b_e065.hcd
```
```
sudo cp fw-105b_e065.hcd /lib/firmware/brcm/BCM43142A0-105b-e065.hcd
``````
tar -zxf bluetooth-3.16-2.tar.gz
```
```
cd bluetooth
```
```
cp /boot/config-$(uname -r) .config
```
```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
```
```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```
```
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```

See if it works, if it doesn't post the result of ```
dmesg | tail
```

---

### Post by Pilot6 on 2015-04-27
jeremy,

It is a wrong way to fix these issues. It is better to make a launchpad bug report, and I will try to fix it upstream.

---

### Post by jeremy31 on 2015-04-27
> **Pilot6 said:**
> jeremy,

It is a wrong way to fix these issues. It is better to make a launchpad bug report, and I will try to fix it upstream.

The posters are free to file bug reports at launchpad.  Is there a way to do a diff against bluetooth-next without downloading everything as I am not on an unlimited internet plan

If you want a list of Broadcom VID/PID's that need patchram support
```
[TABLE]
		[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e032[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21e3[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21e1[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21e8[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e047[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e046[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21ec[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]2003[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e042[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e04f[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3384[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21e6[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21f3[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21f4[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e052[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21d3[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21d6[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21d7[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21d8[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3388[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3389[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0b05[/TD]
		[TD="align: left"]17b5[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]021e[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e055[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3392[/TD]
	[/TR]
	[TR]
		[TD="align: left"]413c[/TD]
		[TD="align: left"]8197[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]2004[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]2005[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e059[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21dc[/TD]
	[/TR]
	[TR]
		[TD="align: left"]105b[/TD]
		[TD="align: left"]e065[/TD]
	[/TR]
	[TR]
		[TD="align: left"]105b[/TD]
		[TD="align: left"]e066[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21de[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]2006[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]2007[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]2009[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3404[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]021f[/TD]
	[/TR]
	[TR]
		[TD="align: left"]413c[/TD]
		[TD="align: left"]8143[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0b05[/TD]
		[TD="align: left"]17cb[/TD]
	[/TR]
	[TR]
		[TD="align: left"]050d[/TD]
		[TD="align: left"]065a[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e062[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e07a[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]200a[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]200b[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]200c[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]200e[/TD]
	[/TR]
	[TR]
		[TD="align: left"]04ca[/TD]
		[TD="align: left"]200f[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0b05[/TD]
		[TD="align: left"]17cf[/TD]
	[/TR]
	[TR]
		[TD="align: left"]145f[/TD]
		[TD="align: left"]01a3[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]0221[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21fb[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21fd[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21fe[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3411[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3413[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3418[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3427[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]0223[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]0225[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]0226[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]2167[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]2168[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]2169[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]216a[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]216b[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]216c[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3435[/TD]
	[/TR]
	[TR]
		[TD="align: left"]13d3[/TD]
		[TD="align: left"]3456[/TD]
	[/TR]
	[TR]
		[TD="align: left"]185f[/TD]
		[TD="align: left"]2167[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e079[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0489[/TD]
		[TD="align: left"]e087[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0930[/TD]
		[TD="align: left"]0229[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]216e[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]216f[/TD]
	[/TR]
	[TR]
		[TD="align: left"]19ff[/TD]
		[TD="align: left"]0239[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0b05[/TD]
		[TD="align: left"]180a[/TD]
	[/TR]
	[TR]
		[TD="align: left"][/TD]
		[TD="align: left"][/TD]
	[/TR]
	[TR]
		[TD="align: left"][/TD]
		[TD="align: left"][/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]216d[/TD]
	[/TR]
	[TR]
		[TD="align: left"]0a5c[/TD]
		[TD="align: left"]21f1[/TD]
	[/TR]
[/TABLE]

```

---

### Post by SA6 on 2015-04-27
> **jeremy31 said:**
> SA6


See if it works, if it doesn't post the result of ```
dmesg | tail
```

Thanks jeremy31! It works now :D

---

### Post by Pilot6 on 2015-04-28
Jeremy31,

These codes won't be added in bulk. Each device should be reported and tested. It is better ti gert people report it properly abd fix the code upstream. It will get to Ubuntu kernel in updates. You just built btusb.ko, after user updates kernel, he or she will need to do it again. It is not a fix at all.
Temporary fix may be to create a dkms module with updated btusb and firmware and place it in ppa.

BTW 0a5c VID has been added for all Broadcom modules. It is backported to Ubuntu kernels already.

---

### Post by jeremy31 on 2015-04-28
> **SA6 said:**
> Thanks jeremy31! It works now :D

Like Pilot6 has stated, if you get a new kernel in an update you will need to build a new module

```
cd bluetooth
```
```
make -C /lib/modules/$(uname -r)/build M=$PWD clean
```
```
cp /boot/config-$(uname -r) .config
```
```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
```
```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```
```
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```


Pilot6, not too many people have the time to wait on the bug reporting process.   This bug report should be an easy one [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1449730](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1449730)

It isn't in bluetooth-next and a very good chance it is AR3012

---

### Post by Pilot6 on 2015-04-29
jeremy31,

It does not take much time to report a bug. It can be fastly fixed, and this fix will help all users. If not report bugs, fixes will never get into the kernel.

That report is incomplete. We need output of

usb-devices

to make a commit.

---

### Post by SA6 on 2015-04-29
My bluetooth taskbar icon has disappeared and it has stopped working. I think I messed something up.

> Linux SA6-Z510 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
	Kernel driver in use: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo Device [17aa:0611]
	Kernel driver in use: wl
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 105b:e065  
Bus 003 Device 004: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 003: ID 1915:7777 Nordic Semiconductor ASA 
Bus 003 Device 002: ID 5986:029d Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    4.421574] Bluetooth: Core ver 2.19
[    4.421585] Bluetooth: HCI device and connection manager initialized
[    4.421592] Bluetooth: HCI socket layer initialized
[    4.421593] Bluetooth: L2CAP socket layer initialized
[    4.421599] Bluetooth: SCO socket layer initialized
[    6.472015] Bluetooth: hci0 command 0x1001 tx timeout
[   14.468050] Bluetooth: hci0: HCI_OP_READ_LOCAL_VERSION failed (-110)
[   14.472081] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=0000 lmp_ver=06 lmp_subver=210b
[   14.927056] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=00d7 lmp_ver=06 lmp_subver=210b
[    0.200818] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.438878] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x595f03)
[    4.924574] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   14.927056] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=00d7 lmp_ver=06 lmp_subver=210b
bluetooth             446409  2 btusb
6lowpan_iphc           18702  1 bluetooth


Update: 

Got this: 
> rfkill list
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


so I ran rfkill unblock. That didn't help.

Then...

> hcitool scan
Scanning ...


hcitool scan returned nothing. 

> hcitool inq
Inquiring ...


hcitool inq returned nothing. 

> hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 9C:D2:1E:F1:B1:A8  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING 
	RX bytes:1522 acl:0 sco:0 events:187 errors:0
	TX bytes:29238 acl:0 sco:0 commands:182 errors:0


---

### Post by SA6 on 2015-04-29
.

---

### Post by jeremy31 on 2015-04-30
I wonder why bnep didn't load?  Have you rebooted?  try ```
sudo modprobe -r btusb
``````
sudo modprobe btusb
```

---

### Post by SA6 on 2015-04-30
Yeah I've rebooted a bunch of times, mostly because the laptop won't wake up from sleep (but that's a different problem :P)

Got this:

> sudo modprobe btusb
Can't init device hci0: Operation not possible due to RF-kill (132)
modprobe: ERROR: ../libkmod/libkmod-module.c:959 command_do() Error running install command for btusb
modprobe: ERROR: could not insert 'btusb': Operation not permitted

> rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

 rfkill unblock 1
rfkill unblock 5

sudo modprobe btusb
Can't init device hci0: Operation not possible due to RF-kill (132)
modprobe: ERROR: ../libkmod/libkmod-module.c:959 command_do() Error running install command for btusb
modprobe: ERROR: could not insert 'btusb': Operation not permitted

rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no



---

### Post by jeremy31 on 2015-04-30
I would see if this removes the soft blocks ```
sudo rfkill unblock all
```

---

### Post by SA6 on 2015-04-30
This removed the soft blocks: 

> rfkill unblock all

rfkill list
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

sudo modprobe btusb
Can't init device hci0: Connection timed out (110)
modprobe: ERROR: ../libkmod/libkmod-module.c:959 command_do() Error running install command for btusb
modprobe: ERROR: could not insert 'btusb': Operation not permitted

now the cursor blinks for a while then times out.

---

### Post by SA6 on 2015-05-01
Looks like it fixed itself after I rebooted into windows 8.1 (i'm on dual boot), then rebooted into linux twice. 

```
hcitool scan
Scanning ...
	BC:F5:AC:02:FA:6D	Nexus 4

```

It won't detect my fake ps3 gamepad though, but I guess that's yet another problem.

---

### Post by 3Kmzx74 on 2015-06-06
jeremy31,
thanks a lot! Worked like a charm :D I've spent 2 days working on this and this is _the only_ solution that works and is permanent (works after reboot, though sometimes i have to manually reload btusb - no idea why...).

-- 
Michal Grabowski

---

### Post by ags40 on 2015-08-15
It did work for me. Thank you very, very much!

---

### Post by stephan13 on 2015-10-16
Hi,

i have the same problem on my Lenovo G40-70. None of the fixes from this thread worked. (i rolled back changes from post #5 already). Im on ubuntu 15.04.

Post #16 fails with an error after the make command.
Here is my output for uname:

stephan@notebook:~/bluetooth$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux notebook 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380a]
	Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 13d3:5727 IMC Networks 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 248a:8566  
Bus 001 Device 002: ID 1241:a1c3 Belkin 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.548745] usb 1-7: Product: Bluetooth Radio 
[    2.699343] Bluetooth: Core ver 2.20
[    2.699362] Bluetooth: HCI device and connection manager initialized
[    2.699367] Bluetooth: HCI socket layer initialized
[    2.699370] Bluetooth: L2CAP socket layer initialized
[    2.699376] Bluetooth: SCO socket layer initialized
[    6.599210] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.599215] Bluetooth: BNEP filters: protocol multicast
[    6.599220] Bluetooth: BNEP socket layer initialized
[    6.621822] Bluetooth: RFCOMM TTY layer initialized
[    6.621833] Bluetooth: RFCOMM socket layer initialized
[    6.621839] Bluetooth: RFCOMM ver 1.11
[   60.938270] Modules linked in: ctr ccm binfmt_misc rfcomm bnep snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic arc4 rtsx_usb_ms memstick intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd fglrx(POE) serio_raw uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common rtl8723be joydev videodev btcoexist media rtl8723_common rtl_pci rtlwifi mac80211 snd_hda_intel snd_soc_rt5640 snd_hda_controller snd_soc_rl6231 i915 snd_hda_codec snd_soc_core snd_hwdep snd_compress lpc_ich snd_pcm_dmaengine amd_iommu_v2 cfg80211 snd_pcm drm_kms_helper ideapad_laptop sparse_keymap btusb drm mei_me bluetooth mei shpchp i2c_algo_bit snd_seq_midi
[    0.165490] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.506214] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x694f03)
[    2.779030] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    5.228137] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
bluetooth             491520  22 bnep,btusb,rfcomm

Can anybody help here ?

---

### Post by jeremy31 on 2015-10-16
This has worked for those who tried it ```
[COLOR=#000000]*sudo add-apt-repository ppa:hanipouspilot/rtlwifi*[/COLOR]
[COLOR=#000000]*sudo apt-get update*[/COLOR]
[COLOR=#000000][I]sudo apt-get install rtlwifi-new-dkms linux-firmware rtl8723au-bt-dkms
```

Reboot and see if bluetooth works[/I][/COLOR]

---

### Post by Mustafa_Khan on 2015-10-16
Same issue.  Any help is appreciated.  I don't know where to find the .hcd file for my device because the vendor and device IDs are completely different from what has been listed in this thread.  Here's my output

```
mustafa@mustafa-ThinkPad:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetoothLinux mustafa-ThinkPad 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5100]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]
    Kernel driver in use: wl
Bus 002 Device 003: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04ca:2007 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 056a:0084 Wacom Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   17.861558] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   18.476156] Bluetooth: Core ver 2.17
[   18.476195] Bluetooth: HCI device and connection manager initialized
[   18.476205] Bluetooth: HCI socket layer initialized
[   18.476208] Bluetooth: L2CAP socket layer initialized
[   18.476213] Bluetooth: SCO socket layer initialized
[   18.594409] Bluetooth: can't load firmware, may not work correctly
[   26.756257] Bluetooth: RFCOMM TTY layer initialized
[   26.756273] Bluetooth: RFCOMM socket layer initialized
[   26.756279] Bluetooth: RFCOMM ver 1.11
[   26.981195] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.981199] Bluetooth: BNEP filters: protocol multicast
[   26.981209] Bluetooth: BNEP socket layer initialized
[    0.003963] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.185513] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.198829] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.212063] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.233730] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.351513] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.351532] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.351803] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.351822] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.462787] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    9.271021] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   18.593577] usb 4-1: Direct firmware load failed with error -2
[   18.594409] Bluetooth: can't load firmware, may not work correctly
bluetooth             391136  22 bnep,btusb,rfcomm
```

---

### Post by Pilot6 on 2015-10-17
This is how to get hcd file.[URL="http://askubuntu.com/a/632348/167850"]

http://askubuntu.com/a/632348/167850[/URL]

---

### Post by ovetomash on 2016-02-01
It's looks like my problem.

Just buy new bt headset and cant use it.

dmesg | grep -i bluetooth
```


[   20.094291] Bluetooth: Core ver 2.20
[   20.094302] Bluetooth: HCI device and connection manager initialized
[   20.094305] Bluetooth: HCI socket layer initialized
[   20.094307] Bluetooth: L2CAP socket layer initialized
[   20.094310] Bluetooth: SCO socket layer initialized
[   20.234701] Bluetooth: hci0: BCM: chip id 63
[   20.235693] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1484
[   20.313209] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0489-e042.hcd failed with error -2
[   20.313213] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0489-e042.hcd not found


```

Can't compile - make -C /lib/modules/$(uname -r)/build M=$PWD modules

```

ove@Yx80:~/bluetooth$ make -C /lib/modules/$(uname -r)/build M=$PWD modules
make: &#1074;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; «/usr/src/linux-source-4.2.0»
  CC [M]  /home/ove/bluetooth/hci_vhci.o
/home/ove/bluetooth/hci_vhci.c:352:2: error: unknown field ‘aio_write’ specified in initializer
  .aio_write = vhci_write,
  ^
/home/ove/bluetooth/hci_vhci.c:352:15: warning: initialization from incompatible pointer type [-Wincompatible-pointer-types]
  .aio_write = vhci_write,
               ^
/home/ove/bluetooth/hci_vhci.c:352:15: note: (near initialization for ‘vhci_fops.write’)
scripts/Makefile.build:264: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1103; &#1088;&#1077;&#1094;&#1077;&#1087;&#1090;&#1072; &#1076;&#1083;&#1103; &#1094;&#1077;&#1083;&#1080; «/home/ove/bluetooth/hci_vhci.o»
make[1]: *** [/home/ove/bluetooth/hci_vhci.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
Makefile:1398: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1103; &#1088;&#1077;&#1094;&#1077;&#1087;&#1090;&#1072; &#1076;&#1083;&#1103; &#1094;&#1077;&#1083;&#1080; «_module_/home/ove/bluetooth»
make: *** [_module_/home/ove/bluetooth] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make: &#1074;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; «/usr/src/linux-source-4.2.0»
ove@Yx80:~/bluetooth$ sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
cp: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; stat &#1076;&#1083;&#1103; «btusb.ko»: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;



```

It's Lenovo y480 laptop and Ubuntu 15.10 (wily) kernel 4.2.6

Fixed by [http://askubuntu.com/a/632348/167850](http://askubuntu.com/a/632348/167850) receipt.

```

ove@Yx80:~$ dmesg | grep -i bluetooth
[   14.558840] Bluetooth: Core ver 2.20
[   14.558857] Bluetooth: HCI device and connection manager initialized
[   14.558861] Bluetooth: HCI socket layer initialized
[   14.558864] Bluetooth: L2CAP socket layer initialized
[   14.558874] Bluetooth: SCO socket layer initialized
[   14.737373] Bluetooth: hci0: BCM: chip id 63
[   14.738373] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   15.977460] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1072


```

But still no sound.

---

### Post by lbelloeil on 2016-08-20
Same issue on Tosiba Satellite Pro c70-A-130  :
```
lolo@lolo-tosh:~$ sudo modprobe btusb
[sudo] Mot de passe de lolo : 
lolo@lolo-tosh:~$ dmesg | grep -i bluetooth
[    3.298272] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[    4.940240] Bluetooth: Core ver 2.21
[    4.940272] Bluetooth: HCI device and connection manager initialized
[    4.940275] Bluetooth: HCI socket layer initialized
[    4.940278] Bluetooth: L2CAP socket layer initialized
[    4.940283] Bluetooth: SCO socket layer initialized
[    5.993242] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.993246] Bluetooth: BNEP filters: protocol multicast
[    5.993250] Bluetooth: BNEP socket layer initialized
[  359.487341] Bluetooth: RFCOMM TTY layer initialized
[  359.487348] Bluetooth: RFCOMM socket layer initialized
[  359.487364] Bluetooth: RFCOMM ver 1.11
[ 1405.707373] Bluetooth: hci0 command 0x0401 tx timeout
```

---

### Post by jeremy31 on 2016-08-22
> **lbelloeil said:**
> Same issue on Tosiba Satellite Pro c70-A-130  :
lolo@lolo-tosh:~$ sudo modprobe btusb
[sudo] Mot de passe de lolo : 
lolo@lolo-tosh:~$ dmesg | grep -i bluetooth
[    3.298272] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[    4.940240] Bluetooth: Core ver 2.21
[    4.940272] Bluetooth: HCI device and connection manager initialized
[    4.940275] Bluetooth: HCI socket layer initialized
[    4.940278] Bluetooth: L2CAP socket layer initialized
[    4.940283] Bluetooth: SCO socket layer initialized
[    5.993242] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.993246] Bluetooth: BNEP filters: protocol multicast
[    5.993250] Bluetooth: BNEP socket layer initialized
[  359.487341] Bluetooth: RFCOMM TTY layer initialized
[  359.487348] Bluetooth: RFCOMM socket layer initialized
[  359.487364] Bluetooth: RFCOMM ver 1.11
[ 1405.707373] Bluetooth: hci0 command 0x0401 tx timeout

Please post the result of ```
lsusb; lspci -nnk | grep -iA2 net; dmesg | egrep -i 'blue|firm'
```
Thanks

---

### Post by sooofye on 2016-09-03
Hi

I have exactly the same problem... If someone could help me !

```

Linux superOrdiDeMoi 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel driver in use: wl

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 002: ID 05c8:0389 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[    7.281881] Bluetooth: Core ver 2.21
[    7.281899] Bluetooth: HCI device and connection manager initialized
[    7.281902] Bluetooth: HCI socket layer initialized
[    7.281905] Bluetooth: L2CAP socket layer initialized
[    7.281910] Bluetooth: SCO socket layer initialized
[    7.289388] Bluetooth: HCI UART driver ver 2.3
[    7.289390] Bluetooth: HCI UART protocol H4 registered
[    7.289392] Bluetooth: HCI UART protocol BCSP registered
[    7.289393] Bluetooth: HCI UART protocol LL registered
[    7.289394] Bluetooth: HCI UART protocol ATH3K registered
[    7.289395] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    7.289427] Bluetooth: HCI UART protocol Intel registered
[    7.289441] Bluetooth: HCI UART protocol BCM registered
[    7.289442] Bluetooth: HCI UART protocol QCA registered
[    7.435366] Bluetooth: hci0: BCM: chip id 70
[    7.452146] Bluetooth: hci0: BCM43142A
[    7.452151] Bluetooth: hci0: BCM (001.001.011) build 0000
[    7.459561] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    7.459566] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    8.492016] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.492020] Bluetooth: BNEP filters: protocol multicast
[    8.492024] Bluetooth: BNEP socket layer initialized
[  213.829069] Bluetooth: hci0 urb ffff880263578d80 failed to resubmit (2)
[  228.774433] Bluetooth: hci0: BCM: chip id 70
[  228.790486] Bluetooth: hci0: superOrdiDeMoi
[  228.790492] Bluetooth: hci0: BCM (001.001.011) build 0000
[  228.790525] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[  228.790527] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[  230.795891] Bluetooth: hci0 command 0x1003 tx timeout

[    0.170635] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    7.459561] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[  228.790525] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2

bluetooth             520192  26 bnep,btbcm,btqca,btrtl,btusb,hci_uart,btintel


```

Thank you

---

### Post by Pilot6 on 2016-09-04
You need to install firmware. See this answer.

[http://askubuntu.com/a/632348/167850](http://askubuntu.com/a/632348/167850)

---

