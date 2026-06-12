---
title: "WiFi does not work with new motherboard | mt7921e is not initialized"
date: 2023-05-16
forum: Hardware
---

### Post by pltpltplt on 2023-05-16
Hello all,

I have installed Windows 11 Pro and Ubuntu 23.04 on a new system. Unfortunately, I can't get the on-board WiFi to work and an external card won't fit. The motherboard in question is the PRO B650M-A WIFI motherboard. I have read about similar (but not the same) errors in other forums and have already tried the following things:


[LIST]
[*]Ubuntu reinstalled with third party software.
[*]installed Ubuntu 22.04 and 22.10
[*]BIOS reset (battery removed)
[*]Secure-Boot disabled
[*]sudo modprobe -r mt7921e
[*]sudo modprobe mt7921e
[*]rfkill unblock
[/LIST]

... unfortunately all without success.

Here is more information:
```

@ubuntu:~$ nmcli radio wifi
enabled

@ubuntu:~$ nmcli device
DEVICE   TYPE      STATE               CONNECTION                  
enp12s0  ethernet  verbunden           Kabelgebundene Verbindung 1 
lo       loopback  verbunden (extern)  lo

@ubuntu:~$ iwconfig
lo        no wireless extensions.
enp12s0   no wireless extensions.

@ubuntu:~$ uname -a 
Linux ubuntu 6.2.0-20-generic #20-Ubuntu SMP PREEMPT_DYNAMIC Thu Apr  6 07:48:48 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

@ubuntu:~$ lspci -knn | grep Net -A2
0d:00.0 Network controller [0280]: MEDIATEK Corp. MT7922 802.11ax PCI Express Wireless Network Adapter [14c3:0616]
 Subsystem: MEDIATEK Corp. MT7922 802.11ax PCI Express Wireless Network Adapter [14c3:0616]
 Kernel modules: mt7921e
0e:00.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Device [1022:43f7] (rev 01)

@ubuntu:~$ lsmod | grep mt7921e
mt7921e                28672  0
mt7921_common         114688  1 mt7921e
mt76_connac_lib        90112  2 mt7921e,mt7921_common
mt76                  122880  3 mt7921e,mt7921_common,mt76_connac_lib

@ubuntu:~$ sudo dmesg | grep mt7921e
[   67.047660] mt7921e 0000:0d:00.0: enabling device (0000 -> 0002)
[   68.251282] mt7921e 0000:0d:00.0: driver own failed [COLOR=#000000][FONT=&amp][   68.251327] mt7921e: probe of 0000:0d:00.0 failed with error -5
[/FONT][/COLOR]
```

---

### Post by morrownr on 2023-05-18
> MEDIATEK Corp. MT7922 802.11ax PCI Express Wireless Network Adapter [14c3:0616]

I have a PCIe card that uses the mt7922 chipset. It was plug and play on Ubuntu 23.04 here. It has a PCI_ID=14C3:7922.

That 0616 sounds like the AMD rebranded version.

Do you want to go digging into the kernel to see if your PCI_ID is there?

It should not be a problem but keep in mind that the mt7921 and mt7922 use different firmware files.

[https://github.com/morrownr/USB-WiFi/blob/main/home/How_to_Install_Firmware_for_Mediatek_based_USB_WiFi_adapters.md](https://github.com/morrownr/USB-WiFi/blob/main/home/How_to_Install_Firmware_for_Mediatek_based_USB_WiFi_adapters.md)

---

