---
title: "Hp Pavillion no bluetooth adapters present eventhough I have one"
date: 2009-12-09
forum: Hardware
---

### Post by myromance123 on 2009-12-09
Hey there, I can't seem to get Bluetooth working on my HP Pavilion dv3500 laptop.

 It would seem the wireless card and bluetooth are one and the same (if thats possible.) This is because the button which I swipe to switch on wireless also switches on bluetooth and switches it off if I swipe it again (its one of those touch sensitive light buttons).

 I'm using Ubuntu 9.10. Thankfully 9.10 solved my problem of having the button not functioning thus my wireless always being disabled in Ubuntu and having to go into Vista to switch it back on... (odd eh?).

 How would I get bluetooth detected and up and running?
I wish to use it to connect to my Nokia XpressMusic phone.

Any help is gratefully appreciated :D

---

### Post by myromance123 on 2009-12-10
Bump.

 I googled and asked and binged and yahoo!ed but found nothing that helped.
I tried some of the bluetooth managers from the repositories but they all don't work?
  I do not know why...

---

### Post by gfraize8701 on 2009-12-30
By chance, has any one found a fix for this?



I've running karmic

root@benny:~# dmesg | grep -i blue
[    0.292015] Bluetooth: Core ver 2.15
[    0.292051] Bluetooth: HCI device and connection manager initialized
[    0.292051] Bluetooth: HCI socket layer initialized
[    1.377434] Bluetooth: L2CAP ver 2.13
[    1.377436] Bluetooth: L2CAP socket layer initialized
[    1.377440] Bluetooth: SCO (Voice Link) ver 0.6
[    1.377443] Bluetooth: SCO socket layer initialized
[    1.377529] Bluetooth: RFCOMM TTY layer initialized
[    1.377534] Bluetooth: RFCOMM socket layer initialized
[    1.377536] Bluetooth: RFCOMM ver 1.11
root@benny:~# hcitool dev
Devices:
root@benny:~# lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
root@benny:~# lsusb
Bus 001 Device 002: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@benny:~#


-Greg

---

### Post by Harutyun Dr. on 2010-01-24
Anyone found how to fix it??? Really need solution for this issue!

---

### Post by Harutyun Dr. on 2010-01-25
I have fixed it! Just remembered that on my vista I could enable/disable wifi/bluetooth in Wireless Assistant separately and thought that enabling bluetooth under vista may somehow activate bluetooth device. And that worked! After rebooting to Ubuntu I saw bluetooth icon with all functions enabled. Haven't used it yet but I think it should work now.

---

### Post by Kulgan on 2010-03-06
> **Harutyun Dr. said:**
> I have fixed it! Just remembered that on my vista I could enable/disable wifi/bluetooth in Wireless Assistant separately and thought that enabling bluetooth under vista may somehow activate bluetooth device. And that worked! After rebooting to Ubuntu I saw bluetooth icon with all functions enabled. Haven't used it yet but I think it should work now.

Thanks for posting that - wouldn't have thought of it! :D
This worked for me too, on a Dell Studio 1537. 

Had to install the bluetooth from Dell as I had done a fresh install of Windows 7 - Vista driver worked fine.

Tested link with jailbroken iPhone - successful file transfer. 

Thanks, folks!

---

### Post by myromance123 on 2010-03-29
To Harutyun Dr. and Kulgan,
 in 8.10 and 9.04 I did that to make my WiFi work ( I dual boot Vista and Ubuntu). It worked for the WiFi (No longer necessary for 9.10 and above).

 Regarding the bluetooth, it made no difference (when I was using 9.04 and 9.10).

 Currently I am using Ubuntu 10.04 Beta 1. I might give that a go again.
Thanks for posting what you guys did though, hopefully it will help others :)

---

### Post by magic_din on 2010-05-08
HP compaq 6535s problwm of bluetooth is also solved in same way. switch on bluetoothe from wireless managaer of windows and then switching to Ubuntu. 
It will not give the error as " the bluetooth adapter is not present." and will work fine........... 
thanks for your help...

---

