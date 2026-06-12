---
title: "bluetooth on Toshiba Satellite L750 with ubuntu 14.10"
date: 2015-05-02
forum: Hardware
---

### Post by stavros5 on 2015-05-02
I am having trouble getting bluetooth to work on my Toshiba Satellite running 14.10. Anybody can help?


# rfkill list 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
#


Thanks,
Stavros

---

### Post by jeremy31 on 2015-05-02
post the results of ```
uname -a; rfkill list all; lsmod | grep bluetooth; lsusb; lspci -nnk | grep -iA2 net; dmesg | grep -i bluetooth; dmesg | grep firmware
```

And we will see what can be done

---

### Post by stavros5 on 2015-05-02
Hey Jeremy,

# uname -a; rfkill list all; lsmod | grep bluetooth; lsusb; lspci -nnk | grep -iA2 net; dmesg | grep -i bluetooth; dmesg | grep firmware
Linux ubuntu-red 3.16.0-36-generic #48-Ubuntu SMP Tue Apr 14 20:08:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
bluetooth             446190  6 bnep,ath3k,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
toshiba_bluetooth      12867  0 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0930:0215 Toshiba Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6613]
	Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fc50]
	Kernel driver in use: atl1c
[    9.802425] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[    9.802482] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   10.924697] Bluetooth: Core ver 2.19
[   10.924716] Bluetooth: HCI device and connection manager initialized
[   10.924724] Bluetooth: HCI socket layer initialized
[   10.924727] Bluetooth: L2CAP socket layer initialized
[   10.924736] Bluetooth: SCO socket layer initialized
[   13.586479] Bluetooth: RFCOMM TTY layer initialized
[   13.586489] Bluetooth: RFCOMM socket layer initialized
[   13.586494] Bluetooth: RFCOMM ver 1.11
[   14.210324] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.210328] Bluetooth: BNEP filters: protocol multicast
[   14.210336] Bluetooth: BNEP socket layer initialized
[   16.557810] Bluetooth: Can't change to loading configuration err
root@ubuntu-red:~#

---

### Post by jeremy31 on 2015-05-02
I am thinking that the current code might be incorrect

```
sudo apt-get install build-essential linux-headers-generic
```
```
wget https://www.dropbox.com/s/4rqrbqr3v9fhma9/bluetooth-stavros.tar.gz
```
```
[COLOR=#111111][FONT=Consolas]tar -zxf bluetooth-stavros.tar.gz
```
```
cd bluetooth
```
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]cp /boot/config-$(uname -r) .config
```
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
```
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]make -C /lib/modules/$(uname -r)/build M=$PWD modules
```
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo cp ath3k.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```

Reboot and see the results[/FONT][/COLOR]

---

### Post by stavros5 on 2015-05-02
bluetooth/btusb.c:338:3: error: implicit declaration of function ‘hci_recv_fragment’ [-Werror=implicit-function-declaration]
   if (hci_recv_fragment(hdev, HCI_EVENT_PKT,
   ^
cc1: some warnings being treated as errors
scripts/Makefile.build:263: recipe for target '/root/blah/bluetooth/btusb.o' failed
make[1]: *** [/root/blah/bluetooth/btusb.o] Error 1
Makefile:1394: recipe for target '_module_/root/blah/bluetooth' failed
make: *** [_module_/root/blah/bluetooth] Error 2

---

### Post by jeremy31 on 2015-05-03
Should file a bug report, start at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by mattharris4 on 2015-05-03
You aren't the only person having this issue with Toshiba laptops.  Unfortunately the only solution any of us could come up with in another thread ( [http://ubuntuforums.org/showthread.php?t=2274915&p=13277989#post13277989](http://ubuntuforums.org/showthread.php?t=2274915&p=13277989#post13277989) ) was to use a USB bluetooth adapter until someone compiles a driver for this bluetooth transmitter.  I wish you the best with this, I don't use bluetooth on my computers but can see where in the next ten years or so instead of using a USB cable to connect devices to a computer we will use this technology to do so.  I do use a bluetooth headset with my cell phone and really like it (admittedly a different bluetooth technology), I do see where this could be a blockbuster technology in the future.  Two other people including a well-respected moderator here have confirmed that bluetooth is built into the Canonical OSes (and Debian itself which is what Canonical builds their OSes on) so it has been thought about by some programmers already even though it is at this point an esoteric technology.

---

### Post by jeremy31 on 2015-05-03
I have a Toshiba P875 and I tried 4 wifi/bt combo cards before the bluetooth even showed up in lsusb.  The one that finally worked was an Atheros AR5B195, it has an Atheros AR9285 wifi with AR3011 bluetooth.  I tried a couple Intel combo cards and another Atheros AR5B225 that had AR9485/AR3012

My other Toshiba was factory equipped with a Wifi/Wimax card and it would be able to find and use bluetooth on my other cards but the wifi was always hard blocked

---

### Post by stavros5 on 2015-05-05
Just wanted to update the thread that with 14.04 LTS it works fine after installing blueman.

---

### Post by mörgæs on 2015-05-05
Thanks for the update.
Developers don't care about 14.10 but if the bug is also present in 15.04 a bug report would be nice.

---

### Post by stavros5 on 2015-05-05
Problem *is* there with 15.04. Tried it before going back to 14.04.

---

