---
title: "Acer Aspire 3003 WLCi with Broadcom 4318 Wi-fi Card"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by Floppyjoe on 2006-12-18
I recently installed edgy to my Acer aspire 3003 WLCi. It has a Broadcom 4318 Wireless card. Some of my programs like wifi radar etc can see my router but I can't get an IP from the router. I'm using ndiswrapper.
  > ndiswrapper -l shows that the hardware and driver are present.

Here is a log file dump.
>  Log of echo Script version: 0.1.2 
Sun Dec 17 14:07:49 2006

Script version: 0.1.2

Sun Dec 17 14:07:49 2006
----------------
Log of lspci 
Sun Dec 17 14:07:49 2006

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

Sun Dec 17 14:07:49 2006
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e 
Sun Dec 17 14:07:49 2006

/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e

Sun Dec 17 14:07:49 2006
----------------
Log of cat /etc/issue 
Sun Dec 17 14:07:49 2006

Ubuntu 6.10 \n \l


Sun Dec 17 14:07:49 2006
----------------
Log of ps -e 
Sun Dec 17 14:07:49 2006

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   86 ?        00:00:00 kseriod
  119 ?        00:00:00 pdflush
  120 ?        00:00:00 pdflush
  121 ?        00:00:00 kswapd0
  122 ?        00:00:00 aio/0
 1702 ?        00:00:00 khubd
 1767 ?        00:00:00 kjournald
 1840 ?        00:00:00 logd
 1986 ?        00:00:00 udevd
 2745 ?        00:00:00 shpchpd
 2831 ?        00:00:00 kpsmoused
 2865 ?        00:00:00 pccardd
 3084 ?        00:00:00 wrap_wq
 3085 ?        00:00:00 ndis_wq
 3525 tty1     00:00:00 getty
 3526 tty2     00:00:00 getty
 3527 tty3     00:00:00 getty
 3528 tty4     00:00:00 getty
 3529 tty5     00:00:00 getty
 3530 tty6     00:00:00 getty
 3739 ?        00:00:00 acpid
 3854 ?        00:00:00 dd
 3856 ?        00:00:00 klogd
 3928 ?        00:00:00 gdm
 3945 ?        00:00:00 gdm
 3948 tty7     00:01:14 Xorg
 3985 ?        00:00:00 hpiod
 3988 ?        00:00:00 python
 4036 ?        00:00:00 dbus-daemon
 4051 ?        00:00:01 hald
 4052 ?        00:00:00 hald-runner
 4058 ?        00:00:00 hald-addon-acpi
 4067 ?        00:00:00 hald-addon-keyb
 4078 ?        00:00:00 hald-addon-keyb
 4092 ?        00:00:00 hald-addon-stor
 4112 ?        00:00:00 dhcdbd
 4129 ?        00:00:00 NetworkManager
 4144 ?        00:00:00 NetworkManagerD
 4162 ?        00:00:00 perl
 4197 ?        00:00:00 ondemand
 4254 ?        00:00:00 hcid
 4261 ?        00:00:00 sdpd
 4276 ?        00:00:00 krfcommd
 4313 ?        00:00:00 atd
 4326 ?        00:00:00 cron
 4469 ?        00:00:00 startkde
 4507 ?        00:00:00 ssh-agent
 4510 ?        00:00:00 dbus-launch
 4511 ?        00:00:00 dbus-daemon
 4529 ?        00:00:00 dhclient3
 4550 ?        00:00:00 start_kdeinit
 4551 ?        00:00:00 kdeinit
 4554 ?        00:00:00 dcopserver
 4557 ?        00:00:00 klauncher
 4559 ?        00:00:02 kded
 4565 ?        00:00:00 kwrapper
 4567 ?        00:00:00 ksmserver
 4568 ?        00:00:02 kwin
 4570 ?        00:00:03 kdesktop
 4572 ?        00:00:07 kicker
 4574 ?        00:00:00 kio_file
 4578 ?        00:00:01 artsd
 4580 ?        00:00:00 kaccess
 4581 ?        00:00:03 gaim
 4586 ?        00:00:43 firefox-bin
 4590 ?        00:00:00 knotify
 4592 ?        00:00:00 klipper
 4605 ?        00:00:00 gconfd-2
 4761 ?        00:00:00 cupsd
 4975 ?        00:00:00 syslogd
 4979 ?        00:00:09 gnome-terminal
 4981 ?        00:00:00 bonobo-activati
 4986 ?        00:00:00 sh
 4987 ?        00:00:00 esd
 4990 ?        00:00:00 gnome-pty-helpe
 4991 pts/1    00:00:00 bash
 5093 ?        00:00:01 konqueror
 5186 ?        00:00:00 kdesud
 5236 ?        00:00:00 dhclient
 5258 ?        00:00:00 dhclient
 5309 ?        00:00:00 kio_media
 5312 pts/1    00:00:00 sh
 5332 pts/1    00:00:00 logsave
 5333 pts/1    00:00:00 ps

Sun Dec 17 14:07:49 2006
----------------
Log of echo Edgy final release detected. 
Sun Dec 17 14:07:49 2006

Edgy final release detected.

Sun Dec 17 14:07:49 2006
----------------
Log of rmmod ndiswrapper 
Sun Dec 17 14:07:49 2006


Sun Dec 17 14:07:49 2006
----------------
Log of rmmod bcm43xx 
Sun Dec 17 14:07:49 2006


Sun Dec 17 14:07:49 2006
----------------
Log of echo Edgy 
Sun Dec 17 14:07:49 2006

Edgy

Sun Dec 17 14:07:49 2006
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8 
Sun Dec 17 14:07:49 2006

Reading package lists...
Building dependency tree...
Reading state information...
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Sun Dec 17 14:07:51 2006
----------------
Log of ndiswrapper -e bcmwl5 
Sun Dec 17 14:07:51 2006

ndiswrapper died with exit status 4

Sun Dec 17 14:07:51 2006
----------------
Log of ndiswrapper -e bcmwl5a 
Sun Dec 17 14:07:51 2006

Driver bcmwl5a is not installed.Use -l to list installed drivers

Sun Dec 17 14:07:52 2006
----------------
Log of ndiswrapper -l 
Sun Dec 17 14:07:52 2006

No drivers installed
ndiswrapper died with exit status 1

Sun Dec 17 14:07:52 2006
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Sun Dec 17 14:07:52 2006

You appear to have an i386 system...installing the i386 drivers...

Sun Dec 17 14:07:52 2006
----------------
Log of tar -xf drivers-32.tar.gz 
Sun Dec 17 14:07:52 2006


Sun Dec 17 14:07:52 2006
----------------
Log of ndiswrapper -i bcmwl5.inf 
Sun Dec 17 14:07:52 2006

Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

Sun Dec 17 14:07:53 2006
----------------
Log of modprobe ndiswrapper 
Sun Dec 17 14:07:53 2006


Sun Dec 17 14:07:54 2006
----------------
Log of iwconfig 
Sun Dec 17 14:07:54 2006

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Sun Dec 17 14:07:54 2006
----------------
Log of ifconfig 
Sun Dec 17 14:07:54 2006

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:CF:53:45  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fecf:5345/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1726439 (1.6 MiB)  TX bytes:210060 (205.1 KiB)
          Interrupt:169 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:14:A4:36:15:2B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:e2000000-e2002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


Sun Dec 17 14:07:54 2006
----------------
Log of iwlist eth1 scan 
Sun Dec 17 14:07:54 2006

eth1      No scan results

Sun Dec 17 14:07:57 2006
----------------
Log of iwlist wlan0 scan 
Sun Dec 17 14:07:57 2006

wlan0     Interface doesn't support scanning.


Sun Dec 17 14:07:57 2006
----------------


any advice would be greatly appreciated. Thanks in advance.

---

### Post by Floppyjoe on 2006-12-18
I just tried "iwlist eth1 scan and got this.
> eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:30:CB:DB
                    ESSID:"WarGames"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:0/100  Signal level:-43 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  


---

### Post by Floppyjoe on 2006-12-22
I played around with it for a while yesterday and could not get it to work but today after booting my laptop up the wireless worked fine for some reason. I don't know what I did right. This post is from my laptop wifi up and running. I hope this info is useful for someone.

---

### Post by kerry_s on 2006-12-23
I just spent 2 days setting up a acer aspire 3500 laptop that i got for $300, Then i found out my wireless card was busted, the radio frequency is broke, so i can't broadcast. I was so frustrated trying to get it to work.

I'm glad your's sorted itself out & hope it stays that way.breakage

---

