---
title: "Toshiba External Hard Drive insufficient available bus power"
date: 2011-03-11
forum: Hardware
---

### Post by TBSPW on 2011-03-11
I have a Toshiba 500GB external hard drive, model: HDDR500E03X and I've been using it for some time on a few of my computers, but lately it hasnt been displaying.

I dont know much about Ubuntu to begin with, so I tried booting back to Vista and I received an error saying that the USB bus does not have enough power, and when I click on the error, it gives a list of USB ports, some bolded that could support the device, and others that cant. (It shows like 14 ports, and I only have 4 in the back and 2 in the front though). I tried plugging it into every USB port on my machine, and unplugging all the other USB devices. Oh, and the little grey power light lights up when its plugged in and I can feel the drive spin up some.

For Ubuntu, I dont know what exactly this all is, but I see at the very bottom a similar error to what I was getting in Windows:

```
bill@bill-desktop:~$ dmesg | tail -n 100
[   25.359340] lirc_dev: IR Remote Control driver registered, major 249 
[   25.360689] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   25.360691] IR LIRC bridge handler initialized
[   25.399963] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.402124]   alloc irq_desc for 42 on node -1
[   25.402127]   alloc kstat_irqs on node -1
[   25.402136] forcedeth 0000:00:07.0: irq 42 for MSI/MSI-X
[   25.402360] eth0: no link during initialization.
[   25.402932] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.545951] svc: failed to register lockdv1 RPC service (errno 97).
[   25.546618] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   25.546859] NFSD: starting 90-second grace period
[   25.733014] hda_codec: ALC1200: BIOS auto-probing.
[   25.733019] hda_codec: ALC1200: SKU not ready 0x411111f0
[   25.733022] hda_codec: Cannot set up configuration from BIOS.  Using base mode...
[   27.828480] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   54.578645] audit_printk_skb: 33 callbacks suppressed
[   54.578649] type=1400 audit(1299896416.602:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1829 comm="apparmor_parser"
[   54.578928] type=1400 audit(1299896416.602:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1829 comm="apparmor_parser"
[   54.605168] ppdev: user-space parallel port driver
[   88.504021] Clocksource tsc unstable (delta = -162882921 ns)
[  249.784476] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[  255.099577] wlan0: authenticate with c0:83:0a:c7:d4:e1 (try 1)
[  255.101092] wlan0: authenticated
[  255.102567] wlan0: associate with c0:83:0a:c7:d4:e1 (try 1)
[  255.105834] wlan0: RX AssocResp from c0:83:0a:c7:d4:e1 (capab=0x431 status=0 aid=1)
[  255.105841] wlan0: associated
[  255.129344] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  255.142943] cfg80211: Calling CRDA for country: US
[  255.150795] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[  255.150804] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[  255.150810] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[  255.150818] cfg80211: Regulatory domain changed to country: US
[  255.150822]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  255.150829]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  255.150836]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  255.150842]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  255.150848]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  255.150854]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  255.150860]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  261.241664] lo: Disabled Privacy Extensions
[  265.505019] wlan0: no IPv6 routers present
[  286.334440] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=26733 DF PROTO=TCP SPT=13777 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  289.430057] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=27191 DF PROTO=TCP SPT=13777 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  295.316718] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=28209 DF PROTO=TCP SPT=13777 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  371.790388] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.240 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=443 DPT=35536 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  374.793588] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.240 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=443 DPT=35536 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  375.194059] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.240 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=443 DPT=35536 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  380.802144] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.240 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=443 DPT=35536 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  381.858895] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.227 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=47967 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  384.882144] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.227 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=47967 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  390.881834] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.227 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=47967 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  391.895974] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.227 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=47967 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  391.966073] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.228 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=40226 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  394.975179] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.228 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=40226 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  395.641729] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.228 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=40226 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  398.986083] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=44734 DF PROTO=TCP SPT=13032 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  400.983082] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.228 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=40226 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  401.580701] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.228 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=443 DPT=40226 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  401.955612] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=45248 DF PROTO=TCP SPT=13032 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  402.912735] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=184.73.211.227 DST=192.168.1.100 LEN=44 TOS=0x00 PREC=0x00 TTL=41 ID=0 DF PROTO=TCP SPT=443 DPT=47967 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
[  408.034778] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=46175 DF PROTO=TCP SPT=13032 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  415.302925] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16580 DF PROTO=TCP SPT=55039 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  418.306042] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16852 DF PROTO=TCP SPT=55039 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  424.348770] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17390 DF PROTO=TCP SPT=55039 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  490.363196] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=59657 DF PROTO=TCP SPT=14318 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  493.229734] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=60118 DF PROTO=TCP SPT=14318 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  499.066346] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=61027 DF PROTO=TCP SPT=14318 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  526.305326] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=26135 DF PROTO=TCP SPT=55458 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  528.967260] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=26403 DF PROTO=TCP SPT=55458 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  534.906318] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=26948 DF PROTO=TCP SPT=55458 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  625.223857] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=19196 DF PROTO=TCP SPT=12517 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  628.500775] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=19700 DF PROTO=TCP SPT=12517 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  634.235372] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=20817 DF PROTO=TCP SPT=12517 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  719.227815] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=36584 DF PROTO=TCP SPT=13199 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  720.252076] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17463 DF PROTO=TCP SPT=56193 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  722.095120] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=37167 DF PROTO=TCP SPT=13199 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  723.426243] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17729 DF PROTO=TCP SPT=56193 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  728.034083] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=38437 DF PROTO=TCP SPT=13199 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  729.365701] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=18278 DF PROTO=TCP SPT=56193 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  835.452744] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=57530 DF PROTO=TCP SPT=12882 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  838.320129] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=58002 DF PROTO=TCP SPT=12882 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  843.388579] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=28630 DF PROTO=TCP SPT=56653 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  844.463838] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=59034 DF PROTO=TCP SPT=12882 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  846.512240] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=28910 DF PROTO=TCP SPT=56653 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  852.451197] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=29466 DF PROTO=TCP SPT=56653 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  863.920301] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.50.104.142 DST=192.168.1.100 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=1788 DF PROTO=TCP SPT=50314 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  866.480172] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.50.104.142 DST=192.168.1.100 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=1867 DF PROTO=TCP SPT=50314 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  872.521894] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.50.104.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=2005 DF PROTO=TCP SPT=50314 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[  933.859857] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=7221 DF PROTO=TCP SPT=13893 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[  939.799190] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=8449 DF PROTO=TCP SPT=13893 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1015.168879] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=19757 DF PROTO=TCP SPT=12391 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1018.141044] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=20130 DF PROTO=TCP SPT=12391 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1023.973940] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=60.171.137.120 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=21057 DF PROTO=TCP SPT=12391 DPT=38383 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1037.162814] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=13303 DF PROTO=TCP SPT=57383 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1040.156364] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=13575 DF PROTO=TCP SPT=57383 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1046.193594] Inbound IN=wlan0 OUT= MAC=00:16:44:75:8e:69:c0:83:0a:c7:d4:e1:08:00 SRC=110.33.17.142 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=14088 DF PROTO=TCP SPT=57383 DPT=38383 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1109.848373] usb 1-8.3: new high speed USB device using ehci_hcd and address 8
[ 1109.941535] usb 1-8.3: rejected 1 configuration due to insufficient available bus power
[ 1109.941542] usb 1-8.3: no configuration chosen from 1 choice

```

So, I took my issue to Google, and I see a lot of references about using a Y-cable to trick my computer into providing more power, but that seems to be for people that got that error straight off the bat, and even then the Y-cables seem to have mixed reviews in working. I've tried the hard drive on my desktop, my laptops, and even a friends computer, and no matter what I use, I get variations of not enough power.

I dont think it could be an actual power issue, because it always worked before.

So... any suggestions about settings that might be wrong? I'm really hoping that the drive itself is ok. (Its about a year and a half old and never got a lot of hard use)

And worst case, does anyone know a way to maybe recover something off the drive? There isnt a whole lot of info on it, but it does have some more of the up to date files that I'd prefer to not go back to my backups on.

(Oh, and really basic steps please! I'm a nerd in windows, but a lost little boy in the world of Linux)

---

### Post by TBSPW on 2011-03-18
So, I broke down and purchased a Y-cable while they were on sale. Still no luck. I'm getting the same unavailable bus power errors in both Windows and Ubuntu. I tried plugging the wires in all different orders and waiting different amounts of time too.

Out of desperation, I took the drive to a school near here and they tried accessing the drive with EnCase forensic software, but without the OS being able to pick up the drive, the program cant find it.

Only idea that anyone has been able to come up with so far is trying to cut the outer case off the drive without hurting the insides and seeing if anything looks wrong in there and maybe trying to connect it internally in the computer. Problem with that is the case is definitely not meant to be opened and I would even know where to begin with cutting it.

Can anyone offer up any suggestions?

---

### Post by wangteng on 2012-06-14
I have same problem with USB-WIDI module.But i use usb-hub. [http://blog.famzah.net/2010/08/11/usb-rejected-1-configuration-due-to-insufficient-available-bus-power/](http://blog.famzah.net/2010/08/11/usb-rejected-1-configuration-due-to-insufficient-available-bus-power/)

---

