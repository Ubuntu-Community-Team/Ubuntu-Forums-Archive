---
title: "[SOLVED] wifi connection problem (with WEP)"
date: 2008-08-23
forum: Hardware
---

### Post by sb2101 on 2008-08-23
Hi Everyone!
After a week break I can not acces the web via my wifi card. It used to work fine before, It worked out of the box after installing 8.04.
I have a static IP, and a WEP pwd. Please find the usual checks posted below. The IP, the network name, the WEP pwd is correct, I have checked them twice (and they are ok under XP).
Could you give me some hints on what to check next? Or can you see anything non usual?
Thanks for help in advance!

BR,
sb2101

*$ lspci*
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
**04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)**
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


*$ lsmod | grep wifi*
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211


*$ ifconfig*
eth0      Link encap:Ethernet  HWaddr 00:1d:72:01:2c:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

[B]eth1      Link encap:Ethernet  HWaddr 00:1c:bf:1b:65:c6  
          inet addr:192.168.50.77  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe1b:65c6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1263119 (1.2 MB)  TX bytes:15026 (14.6 KB)[/B]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83332 (81.3 KB)  TX bytes:83332 (81.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-1B-65-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



*$ more /etc/network/interfaces*
auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider ppp0
auto ppp0

iface eth1 inet static
address 192.168.**.**
netmask 255.255.255.0
gateway 192.168.**.**
wireless-key **********
wireless-essid *********

auto eth1

---

### Post by jasonkirk2006 on 2008-08-28
Hi;

Did you really solved your problem or you marked it as [COLOR="Red"][SOLVED][/COLOR] by mistake? If you solved it, could you please explaint us how? I'm having a similar problem and looking for a solution.

---

### Post by sb2101 on 2008-09-06
Hi jasonkirk2006!

I removed the network manager and installed WICD instead. I can connect now, however not to all the available networks. There are a few network with the same settings in a student hostel. I can't connect to the closest one, but it works with the others... I don't understand why, but at least it is working. So I use it as it is now.

---

