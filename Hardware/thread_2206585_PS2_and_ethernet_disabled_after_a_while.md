---
title: "PS/2 and ethernet disabled after a while"
date: 2014-02-19
forum: Hardware
---

### Post by JustYakov on 2014-02-19
I'm using a computer with Ubuntu 12.04 as a server, and for some reason, after the server runs for about a day, the PS/2 keyboard and ethernet port get disabled. I can't use my keyboard, but if I plug in a USB keyboard, it works fine. Also, I'm not able to connect to the internet, even to the LAN! I wrote a simple script which reboots the computer when it detects there is no internet, but I'm hoping to find a better solution. Any suggestions?

---

### Post by tgalati4 on 2014-02-20
Bad motherboard.  When you have several devices go down, chances are your motherboard is on its way to the recycler.  How old is the machine?  What does dmesg say?

```
dmesg | tail -200
```

Only post errors.

Try cleaning the motherboard, reseating connectors and checking for leaking or bulging capacitors.

---

### Post by JustYakov on 2014-02-20
Thank you, I will try doing this. But I don't quite understand why, after rebooting, everything works fine again.

---

### Post by JustYakov on 2014-02-21
Okay, so I got some outputs.

dmesg:```
[101310.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101322.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101334.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101346.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101358.027038] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101370.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101383.809620] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101394.616013] eth0: no IPv6 routers present
[101399.019081] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[101411.019033] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF

```The rest is pretty much these lines spammed throughout

/var/log/syslog:```
Feb 21 19:41:42 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Feb 21 19:41:43 wjykk dhclient: No DHCPOFFERS received.
Feb 21 19:41:43 wjykk dhclient: No working leases in persistent database - sleeping.
Feb 21 19:41:48 wjykk kernel: [100230.027024] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:42:00 wjykk kernel: [100242.027043] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:42:12 wjykk kernel: [100254.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:42:24 wjykk kernel: [100266.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:42:36 wjykk kernel: [100278.027016] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:42:48 wjykk kernel: [100290.027145] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:43:00 wjykk kernel: [100302.027020] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:43:12 wjykk kernel: [100314.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:43:24 wjykk kernel: [100326.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:43:36 wjykk kernel: [100338.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:43:48 wjykk kernel: [100350.027020] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:44:00 wjykk kernel: [100362.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:44:12 wjykk kernel: [100374.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:44:24 wjykk kernel: [100386.027039] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:44:36 wjykk kernel: [100398.027006] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:44:48 wjykk kernel: [100410.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:44:56 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 21 19:44:56 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:44:59 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 21 19:44:59 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:45:00 wjykk kernel: [100422.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:45:01 wjykk CRON[5339]: (root) CMD (bash /usr/local/reboot.sh)
Feb 21 19:45:01 wjykk CRON[5338]: (CRON) info (No MTA installed, discarding output)
Feb 21 19:45:07 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 21 19:45:12 wjykk kernel: [100434.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:45:22 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Feb 21 19:45:22 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:45:24 wjykk kernel: [100446.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:45:36 wjykk kernel: [100458.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:45:41 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 21 19:45:41 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:45:48 wjykk kernel: [100470.027022] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:45:54 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 21 19:46:00 wjykk kernel: [100482.027183] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:46:08 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Feb 21 19:46:12 wjykk kernel: [100494.027023] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:46:24 wjykk kernel: [100506.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:46:27 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 21 19:46:35 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 21 19:46:36 wjykk kernel: [100518.027028] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:46:47 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 21 19:46:47 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:46:48 wjykk kernel: [100530.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:46:53 wjykk transmission-daemon[1237]: SC4 Deluxe.rar Could not connect to tracker (announcer.c:990)
Feb 21 19:46:53 wjykk transmission-daemon[1237]: SC4 Deluxe.rar Retrying announce in 7220 seconds. (announcer.c:999)
Feb 21 19:47:00 wjykk kernel: [100542.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:47:01 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 19:47:08 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 21 19:47:12 wjykk kernel: [100554.027010] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:47:18 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 21 19:47:24 wjykk kernel: [100566.027020] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:47:32 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Feb 21 19:47:36 wjykk kernel: [100578.027027] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:47:48 wjykk kernel: [100590.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:47:50 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Feb 21 19:48:00 wjykk kernel: [100602.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:48:03 wjykk transmission-daemon[1237]: SC4 Deluxe.rar Could not connect to tracker (announcer.c:990)
Feb 21 19:48:03 wjykk transmission-daemon[1237]: SC4 Deluxe.rar Retrying announce in 7229 seconds. (announcer.c:999)
Feb 21 19:48:11 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 21 19:48:11 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:48:12 wjykk kernel: [100614.027050] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:48:24 wjykk kernel: [100626.027020] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:48:26 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 21 19:48:36 wjykk kernel: [100638.027027] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:48:39 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Feb 21 19:48:48 wjykk kernel: [100650.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:48:58 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Feb 21 19:49:00 wjykk kernel: [100662.027022] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:49:12 wjykk kernel: [100674.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:49:15 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Feb 21 19:49:24 wjykk kernel: [100686.027023] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:49:33 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 21 19:49:36 wjykk kernel: [100698.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:49:47 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 21 19:49:48 wjykk kernel: [100710.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:49:57 wjykk dhclient: No DHCPOFFERS received.
Feb 21 19:49:57 wjykk dhclient: No working leases in persistent database - sleeping.
Feb 21 19:50:00 wjykk kernel: [100722.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:50:12 wjykk kernel: [100734.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:50:24 wjykk kernel: [100746.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:50:36 wjykk kernel: [100758.027028] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:50:48 wjykk kernel: [100770.027007] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:51:00 wjykk kernel: [100782.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:51:12 wjykk kernel: [100794.027028] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:51:24 wjykk kernel: [100806.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:51:36 wjykk kernel: [100818.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:51:48 wjykk kernel: [100830.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:52:00 wjykk kernel: [100842.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:52:12 wjykk kernel: [100854.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:52:24 wjykk kernel: [100866.027105] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:52:36 wjykk kernel: [100878.027021] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:52:48 wjykk kernel: [100890.027020] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:53:00 wjykk kernel: [100902.027022] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:53:12 wjykk kernel: [100914.027016] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:53:24 wjykk kernel: [100926.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:53:36 wjykk kernel: [100938.027008] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:53:48 wjykk kernel: [100950.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:54:00 wjykk kernel: [100962.027022] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:54:12 wjykk kernel: [100974.027029] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:54:24 wjykk kernel: [100986.027040] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:54:36 wjykk kernel: [100998.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:54:48 wjykk kernel: [101010.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:55:00 wjykk kernel: [101022.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:55:12 wjykk kernel: [101034.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:55:24 wjykk kernel: [101046.027016] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:55:36 wjykk kernel: [101058.027157] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:55:48 wjykk kernel: [101070.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:56:00 wjykk kernel: [101082.027015] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:56:12 wjykk kernel: [101094.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:56:23 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 21 19:56:23 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:56:24 wjykk kernel: [101106.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:56:26 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 19:56:26 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:56:33 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 19:56:33 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:56:36 wjykk kernel: [101118.027020] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:56:40 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 21 19:56:48 wjykk kernel: [101130.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:56:54 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 21 19:56:54 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:57:00 wjykk kernel: [101142.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:57:04 wjykk transmission-daemon[1237]: SC4 Deluxe.rar Could not connect to tracker (announcer.c:990)
Feb 21 19:57:04 wjykk transmission-daemon[1237]: SC4 Deluxe.rar Retrying announce in 7205 seconds. (announcer.c:999)
Feb 21 19:57:04 wjykk transmission-daemon[1237]: Win8.1 Could not connect to tracker (announcer.c:990)
Feb 21 19:57:04 wjykk transmission-daemon[1237]: Win8.1 Retrying announce in 7209 seconds. (announcer.c:999)
Feb 21 19:57:05 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 19:57:05 wjykk dhclient: send_packet: No buffer space available
Feb 21 19:57:12 wjykk kernel: [101154.027022] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:57:12 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 21 19:57:24 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Feb 21 19:57:24 wjykk kernel: [101166.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:57:36 wjykk kernel: [101178.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:57:45 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Feb 21 19:57:48 wjykk kernel: [101190.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:58:00 wjykk kernel: [101202.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:58:02 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Feb 21 19:58:12 wjykk kernel: [101214.027029] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:58:18 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 21 19:58:24 wjykk kernel: [101226.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:58:30 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 21 19:58:36 wjykk kernel: [101238.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:58:42 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Feb 21 19:58:48 wjykk kernel: [101250.027023] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:58:51 wjykk transmission-daemon[1237]: Windows XP Pro SP3 - Activated Could not connect to tracker (announcer.c:990)
Feb 21 19:58:51 wjykk transmission-daemon[1237]: Windows XP Pro SP3 - Activated Retrying announce in 7258 seconds. (announcer.c:999)
Feb 21 19:58:59 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Feb 21 19:59:00 wjykk kernel: [101262.027008] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:59:12 wjykk kernel: [101274.027022] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:59:16 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb 21 19:59:24 wjykk kernel: [101286.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:59:25 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Feb 21 19:59:36 wjykk kernel: [101298.027016] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:59:44 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 19:59:48 wjykk kernel: [101310.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 19:59:51 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 19:59:58 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 21 20:00:00 wjykk kernel: [101322.027018] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:00:01 wjykk CRON[5610]: (root) CMD (bash /usr/local/reboot.sh)
Feb 21 20:00:01 wjykk CRON[5609]: (CRON) info (No MTA installed, discarding output)
Feb 21 20:00:10 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 21 20:00:12 wjykk kernel: [101334.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:00:21 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 20:00:24 wjykk kernel: [101346.027019] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:00:28 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 21 20:00:36 wjykk kernel: [101358.027038] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:00:38 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Feb 21 20:00:48 wjykk kernel: [101370.027017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:00:48 wjykk dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Feb 21 20:00:48 wjykk avahi-autoipd(eth0)[2644]: Got SIGTERM, quitting.
Feb 21 20:00:48 wjykk avahi-autoipd(eth0)[2644]: Callout STOP, address 169.254.5.81 on interface eth0
Feb 21 20:00:48 wjykk smbd[2110]: [2014/02/21 20:00:48.503162,  0] param/loadparm.c:7969(lp_do_parameter)
Feb 21 20:00:48 wjykk smbd[2110]:   Ignoring unknown parameter "update encrypted"
Feb 21 20:00:48 wjykk NetworkManager[976]: <info> (eth0): carrier now OFF (device state 10)
Feb 21 20:01:01 wjykk NetworkManager[976]: <info> (eth0): carrier now ON (device state 10)
Feb 21 20:01:01 wjykk kernel: [101383.809620] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:01:01 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 21 20:01:04 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 20:01:11 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 21 20:01:12 wjykk kernel: [101394.616013] eth0: no IPv6 routers present
Feb 21 20:01:17 wjykk kernel: [101399.019081] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:01:25 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 21 20:01:29 wjykk kernel: [101411.019033] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:01:36 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 21 20:01:41 wjykk kernel: [101423.019222] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:01:47 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 21 20:01:53 wjykk kernel: [101435.019034] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:02:00 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Feb 21 20:02:05 wjykk kernel: [101447.019035] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:02:17 wjykk kernel: [101459.019017] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:02:20 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 21 20:02:30 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 21 20:02:40 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 21 20:02:48 wjykk transmission-daemon[1237]: Couldn't connect socket 14 to 59.103.213.43, port 51413 (errno 101 - Network is unreachable) (net.c:284)
Feb 21 20:02:53 wjykk kernel: [101495.019029] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb 21 20:02:53 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 21 20:03:00 wjykk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
```

Extremely weird, I must say.

---

### Post by JustYakov on 2014-02-21
I think this is far more interesting:```
[ 6098.016017] ------------[ cut here ]------------
[ 6098.016031] WARNING: at /build/buildd/linux-3.2.0/net/sched/sch_generic.c:255 dev_watchdog+0x1e6/0x1f0()
[ 6098.016036] Hardware name: PC109A-ABA A630N
[ 6098.016039] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[ 6098.016043] Modules linked in: snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i915 snd drm_kms_helper drm rfcomm soundcore i2c_algo_bit ppdev bnep lp bluetooth psmouse serio_raw usbhid parport_pc hid mac_hid snd_page_alloc video parport 8139too 8139cp usb_storage firewire_ohci firewire_core crc_itu_t
[ 6098.016097] Pid: 0, comm: swapper/0 Not tainted 3.2.0-58-generic #88-Ubuntu
[ 6098.016101] Call Trace:
[ 6098.016110]  [<c104b1e2>] warn_slowpath_common+0x72/0xa0
[ 6098.016117]  [<c149b6d6>] ? dev_watchdog+0x1e6/0x1f0
[ 6098.016122]  [<c149b6d6>] ? dev_watchdog+0x1e6/0x1f0
[ 6098.016128]  [<c104b2b3>] warn_slowpath_fmt+0x33/0x40
[ 6098.016133]  [<c149b6d6>] dev_watchdog+0x1e6/0x1f0
[ 6098.016141]  [<c105827f>] call_timer_fn+0x2f/0x110
[ 6098.016147]  [<c149b4f0>] ? qdisc_reset+0x40/0x40
[ 6098.016153]  [<c105997b>] run_timer_softirq+0xeb/0x200
[ 6098.016158]  [<c149b4f0>] ? qdisc_reset+0x40/0x40
[ 6098.016163]  [<c1051e90>] ? local_bh_enable_ip+0x90/0x90
[ 6098.016168]  [<c1051f11>] __do_softirq+0x81/0x1a0
[ 6098.016175]  [<c157a834>] ? nmi_stack_correct+0x2f/0x34
[ 6098.016180]  [<c1051e90>] ? local_bh_enable_ip+0x90/0x90
[ 6098.016185]  [<c1051e90>] ? local_bh_enable_ip+0x90/0x90
[ 6098.016189]  <IRQ>  [<c1052256>] ? irq_exit+0x76/0xa0
[ 6098.016198]  [<c15817c9>] ? smp_apic_timer_interrupt+0x59/0x88
[ 6098.016204]  [<c157a549>] ? apic_timer_interrupt+0x31/0x38
[ 6098.016211]  [<c14400e0>] ? stripe_iterate_devices+0x20/0x70
[ 6098.016218]  [<c1009d5d>] ? mwait_idle+0x7d/0x1d0
[ 6098.016223]  [<c1001818>] ? cpu_idle+0xa8/0xd0
[ 6098.016229]  [<c1549445>] ? rest_init+0x5d/0x68
[ 6098.016235]  [<c183976b>] ? start_kernel+0x352/0x358
[ 6098.016240]  [<c18393aa>] ? pass_bootoption.constprop.2+0xe2/0xe2
[ 6098.016249]  [<c18390a9>] ? i386_start_kernel+0xa9/0xaf
[ 6098.016253] ---[ end trace cc2e225e427eaba5 ]---
```

---

### Post by tgalati4 on 2014-02-22
Your network card is cutting in and out.  Each *ifup* entry is telling you that the ethernet card is cutting out.  You should only have one of those during a boot or wake/suspend cycle.  The traceback dump in your second post is also related to the ethernet card, set off by the watchdog timer.  The watchdog tries to kill processes that are stuck.  It took out your sound card modules as well since many on-board ethernet chips also control the sound processor as well.

When you reboot, the motherboard cools down and the devices start to work again.  When the motherboard heats up, a connection breaks and you lose some hardware.  Check for leaky or bulging capacitors.  Put your finger on the southbridge chip and estimate the temperature.  If you can't keep your finger on it because it is too hot, then you have found your problem.

Perform a google search on your motherboard and see if others are having similar problems.  How old is the board?

---

