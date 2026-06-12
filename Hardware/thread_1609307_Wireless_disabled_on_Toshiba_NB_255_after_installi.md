---
title: "Wireless disabled on Toshiba NB 255 after installing Ubuntu 10.04 netbook addition"
date: 2010-10-30
forum: Hardware
---

### Post by bryan.sailer on 2010-10-30
Last night I installed the netbook addition of Ubuntu 10.04. The installation went fine and the netbook boots quickly, but the wireless adapter is disabled and I do not have the option to enable wireless. I also use a USB wireless device. The device when plugged in is detected but I do not have the option to enable that device either. I have been runing Ubuntu at home on me Desktop and server for over 8 months not but this is my first netbook install. I have been searching for drivers online and other possible solutions but I have yet to find a resolution. At this point I will try anything. 
 
Bryan Sailer
Ubuntu 10.04
Toshiba netbook NB 255

---

### Post by bryan.sailer on 2010-12-30
When I run the command ifconfig I get the following:
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 88:ae:1d:42:2a:0c  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Interrupt:27 Base address:0xa000[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:156 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:12160 (12.1 KB)  TX bytes:12160 (12.1 KB)[/FONT][/SIZE]
 
and the iwconfig command shows:
 
[FONT=Times New Roman][SIZE=3]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]eth0      no wireless extensions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wlan0     IEEE 802.11bgn  ESSID:"on/any"  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Power Management:on[/FONT][/SIZE]
 
I was able to get the Mode to be managed by modifying the /etc/NetworkManager/nm-system-settings.conf and the /var/lib/NetworkManager/NetworkManager.state. But the Wireless network still shows disabled. Does anyone know what my next step should be to turn my wireless back on.

---

### Post by bryan.sailer on 2011-01-05
The simple solution was to borrow a hard drive with windows installed and turn the wifi back on. Then I replaced the hard drive with Ubuntu linux istalled and the wifi was now enabled on the laptop. Lesson learned is to ensure that you have everything turned on or the new OS will not recognize the device.

---

