---
title: "Unable to use Wi-Fi"
date: 2009-05-05
forum: Hardware
---

### Post by askates on 2009-05-05
I have a Toshiba Satellite L350 laptop I got recently. I was fed up of Vista, so I changed to Ubuntu (9.04 Jaunty Jackalope). I'm completely new to Ubuntu here. I could find my way around Windows, but I was lost in Ubuntu.

I've spent the last 8 hours or so trying to configure my laptop to work... :/ The main issue seems to be I can't connect to any wireless. The wired connection works fine, but where I'd normally get excellent signal, I get nothing. This is more in part due to the fact that the wi-fi doesnt work at all, than a weak signal or anything.

My Wireless card is an Acer AR5BXB63. Google tells me there seems to be a bit of an issue in terms of compatibility with ubuntu... Any suggestions? Wi-fi is a pretty essential feature to me, and I don't want to have to go back to Windows (well, maybe XP. But not Vista.).

Any help would be appreciated.

---

### Post by Dannidy on 2009-08-24
Hello askates i'm sorry to hear that you are having problems      but if it helps any you are not alone   i myself have a toshiba satellite L505D and when i installed ubuntu 9.04 as a dual boot i was mortified that wireless card doesn't work either and from what i have found alot of people are having the same problem without a viable solutiongood luck in your seach and if you find something let me know

---

### Post by utnubuuser on 2009-08-24
This is an issue to take up with the manufacturer.  - Spend the ten minutes to send a report to toshiba and ask them to take more care in hardware selection.
  - Things wont change if the people working at these factories/marketing haven't got documentation from paying customers to back-up their claims that Linux support is worth money to the company.

---

### Post by rttm on 2009-08-29
Had the same issue with no wireless connection on the Toshiba Satellite l350 on Ubuntu 9.04. I got it working by replacing the current network adapter with the lastest wicd v1.6.2 @ [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php). So far its the only solution for now. Hope this help others. Always options

---

### Post by zipperback on 2009-08-29
Please provide the output from the following commands from within a terminal window.

Click Applications -> Accessories -> Terminal

```

lspci
lsusb
iwconfig
ifconfig

```

Thank you.

- zipperback
:popcorn:

---

### Post by rttm on 2009-09-03
Here is the data from the above command yo
us asked for Toshiba Satellite l350
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
bob@bob-laptop:~$ sudo lsusb
Bus 002 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bob@bob-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ASQWZX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:01:9A:16:97   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:6776-358A-AB78-20AF-3823-1EB6-ACD3-997F-BDE9-82E2-6198-BE4D-A560-29F3-C121-34DE [2]   Security mode:open
          Power Management:off
          Link Quality=90/100  Signal level:-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bob@bob-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:d1:e5:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20882 (20.8 KB)  TX bytes:20882 (20.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d2:c7:20:3b  
          inet addr:192.168.15.109  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d2ff:fec7:203b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26397909 (26.3 MB)  TX bytes:4023522 (4.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-D2-C7-20-3B-30-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bob@bob-laptop:~$

---

### Post by zipperback on 2009-09-06
Are you able to access the Internet now? Your output shows that it's got an ip address assigned.

If you are still having a problem let us know.

- zipperback
:popcorn:

---

