---
title: "bluetooth poor signal strength on ubuntu 15.10"
date: 2015-10-31
forum: Hardware
---

### Post by george-panainte on 2015-10-31
Hello,

Since I have upgraded my system from Ubuntu 14.04 to Ubuntu 15.10 I have  issues with my bluetooth. I can connect to my wireless headphones only  if they are very close (10 cm) to my laptop. As soon as I move them  farther away the connection is interrupted and I get the following error  messages in syslog:

```
bluetoothd[699]: Abort: Connection timed out (110)
acpid: input device has been disconnected, fd 21
bluetoothd[699]: Unable to get Headset Voice gateway SDP record: Host is down
```

Using blueman I can see that received signal strength is sub-optimal,  but I have not idea how to fix this. With Ubuntu 14.04 and the same  headphones I had excellent signal quality even at a distance of 5m from  my laptop.

[ATTACH=CONFIG]265310[/ATTACH]

```
$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
0a:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz PRO [Radeon R5 M255]

$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 10:08:B1:2F:93:F4  ACL MTU: 820:8  SCO MTU: 255:16
    UP RUNNING 
    RX bytes:85080 acl:73 sco:0 events:9855 errors:0
    TX bytes:2386672 acl:5407 sco:0 commands:7061 errors:0

$ uname -r
4.2.0-16-generic




```

---

### Post by george-panainte on 2015-11-15
I have solved this issue using the following steps:

1. I have removed the custom module which I had installed for the previous version of Ubuntu ([http://askubuntu.com/questions/685981/cannot-find-bluetooth-devices-atheros-0cf3817b](http://askubuntu.com/questions/685981/cannot-find-bluetooth-devices-atheros-0cf3817b))

```

sudo apt-get remove btusb-lp1506615-dkms
sudo apt-get remove rtlwifi-new-dkms 

```

2. I have reinstalled the stock drivers (which are part of the kernel), then I rebooted the system

```

sudo apt-get install --reinstall linux-image-extra-$(uname -r)
reboot

```

3. I have installed [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)

```

git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new/
sudo make install
reboot

```

---

