---
title: "Need Wireless Help: Presario c700"
date: 2008-09-04
forum: Hardware
---

### Post by moo113 on 2008-09-04
Hi there,

I recently picked up a Presario c700 laptop and I'm wanting to run Ubuntu  (8.04.1)as my primary OS. So far all of my hardware has been recognized and is working...except for my wireless, of course. My Linux knowledge and experience is limited, but I'm great at following directions!

To start, my lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

And my iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have WICD installed (as I need WPA) but I can start from scratch at any point. Currently the Gnome Network Manager recognizes the wireless device, but WICD refuses to. ath0 doesn't yield any result, I can't scan for networks, etc.

---

### Post by iraqb on 2008-09-04
i have same problem

---

### Post by mma8x on 2008-09-10
[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by maddagger on 2008-09-10
I have tried most of the threads to try and get my wireless working and I have only had limited success! went through the process on [http://ubuntuforums.org/showthread.php?p=4999962](http://ubuntuforums.org/showthread.php?p=4999962) and did get the wireless to pickup the local unlocked network, but it wouldn't connect, and after a reboot was back to nothing! This has been soooooo frustrating. I am almost at the point of reinstalling VISTA it is that bad! I have a C742tu and if anybody could help me I would be so thankful.

---

### Post by kspncr on 2008-09-11
I have the same computer and this worked for me: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

