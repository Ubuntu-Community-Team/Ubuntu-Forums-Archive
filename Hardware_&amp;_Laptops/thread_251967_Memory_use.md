---
title: "Memory use"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by shdgrao on 2006-09-06
Hi. I have an Acer Laptop with 512 Mb of ram. My problem is that after reeboting almost all my memory is used and if I start one program it starts using swap memory. Of course, for me this is a problem because I use programs like openoffice or netbeans that use a lot of memory, and running with swap, they go slow. I am attaching the result of the top command.. maybe any of you can see something extrange or just tell me that the situation is normal. 

PD.I am running dapper 32 bits, The Laptop is an Acer Aspire 1500, 3200+ 512 Mb ram.

Thank you in advance.

top - 12:35:54 up 50 min,  2 users,  load average: 0.81, 0.59, 0.55
Tasks:  85 total,   1 running,  84 sleeping,   0 stopped,   0 zombie
Cpu(s): 29.4% us,  1.8% sy,  0.0% ni, 68.2% id,  0.0% wa,  0.5% hi,  0.0% si
Mem:    515308k total,   433248k used,    82060k free,    18880k buffers
Swap:   305192k total,    17984k used,   287208k free,   238008k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6935 pablo     15   0 58720  16m 9.8m S 26.6  3.4   0:36.84 gnome-terminal
 4539 root      15   0 53500  26m  10m S  3.7  5.4   2:58.69 Xorg
 5202 pablo     17   0 19120 9.8m 7396 S  0.6  2.0   0:16.30 sensors-applet
 5159 pablo     15   0 46252 8164 6504 S  0.3  1.6   0:08.33 gnome-cups-icon
 4730 haldaemo  16   0  2012  864  760 D  0.1  0.2   0:00.26 hald-addon-stor
 7447 pablo     16   0  2196 1112  860 R  0.1  0.2   0:00.02 top
    1 root      16   0  1564  528  460 S  0.0  0.1   0:00.96 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:02.82 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  137 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
  140 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.17 kswapd0
  727 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kseriod
 1839 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1852 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1855 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 1954 root      15   0     0    0    0 S  0.0  0.0   0:00.12 kjournald
 2182 root      13  -4  2432  896  344 S  0.0  0.2   0:00.17 udevd
 2986 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3003 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3025 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3184 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 4066 root      16   0  2152 1192  644 S  0.0  0.2   0:00.00 acpid
 4179 root      16   0  1680  496  412 S  0.0  0.1   0:00.02 dd
 4181 klog      16   0  2400 1324  388 S  0.0  0.3   0:00.05 klogd
 4505 root      15   0 10908 1792 1220 S  0.0  0.3   0:00.00 gdm
 4524 root      16   0 11352 2632 1996 S  0.0  0.5   0:00.01 gdm
 4546 hplip     16   0 12872  920  696 S  0.0  0.2   0:00.00 hpiod
 4564 hplip     15   0  9412 4672 1092 S  0.0  0.9   0:00.06 python
 4637 messageb  16   0  2328  928  676 S  0.0  0.2   0:00.13 dbus-daemon
 4652 haldaemo  16   0  6952 5552 1564 S  0.0  1.1   0:01.60 hald
 4653 root      16   0  2720  968  836 S  0.0  0.2   0:00.01 hald-runner
 4658 haldaemo  16   0  2004  792  696 S  0.0  0.2   0:00.00 hald-addon-acpi
 4712 haldaemo  15   0  2008  796  692 S  0.0  0.2   0:00.03 hald-addon-keyb
 4729 haldaemo  16   0  2012  820  716 S  0.0  0.2   0:00.32 hald-addon-stor
 4749 root      15   0  1932  824  688 S  0.0  0.2   0:00.05 dhcdbd
 4768 root      15   0 28520 2100 1732 S  0.0  0.4   0:00.12 NetworkManager
 4781 root      16   0  2924 1292 1048 S  0.0  0.3   0:00.02 NetworkManagerD
 4826 root      16   0  2488 1364  332 S  0.0  0.3   0:00.00 hddtemp
 4858 root      20   5  1556  372  304 S  0.0  0.1   0:00.07 powernowd
 4903 root      18   0  1968  708  616 S  0.0  0.1   0:00.00 hcid
 4907 root      22   0  1620  460  384 S  0.0  0.1   0:00.00 sdpd
 4922 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4935 root      16   0  1624  296  232 S  0.0  0.1   0:00.00 mdadm
 4970 daemon    24   0  1804  400  296 S  0.0  0.1   0:00.00 atd
 4983 root      16   0  2120  840  684 S  0.0  0.2   0:00.00 cron
 5062 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 5063 pablo     15   0 19868  10m 7508 S  0.0  2.0   0:00.64 x-session-manag
 5105 pablo     16   0  4328  688  444 S  0.0  0.1   0:00.00 ssh-agent
 5108 pablo     16   0  2716  656  520 S  0.0  0.1   0:00.00 dbus-launch
 5109 pablo     15   0  2196  988  776 S  0.0  0.2   0:00.16 dbus-daemon
 5111 pablo     16   0  6320 3884 1920 S  0.0  0.8   0:01.20 gconfd-2
 5114 pablo     18   0  2344  740  544 S  0.0  0.1   0:00.00 gnome-keyring-d
 5116 pablo     16   0  6360 2972 2264 S  0.0  0.6   0:00.13 bonobo-activati
 5118 pablo     15   0 27716 9312 7216 S  0.0  1.8   0:01.46 gnome-settings-
 5126 pablo     16   0  5548 4008 1052 S  0.0  0.8   0:00.10 esd
 5131 pablo     15   0 15684 9516 6728 S  0.0  1.8   0:20.56 metacity
 5137 pablo     15   0 45600  18m  13m S  0.0  3.7   0:08.22 gnome-panel
 5139 pablo     15   0 84956  27m  19m S  0.0  5.5   0:08.29 nautilus
 5142 pablo     15   0 17492 5416 4052 S  0.0  1.1   0:00.18 gnome-volume-ma
 5150 pablo     15   0 37020  11m 8104 S  0.0  2.2   0:00.92 update-notifier
 5155 pablo     15   0  8740 3952 3112 S  0.0  0.8   0:00.18 gnome-vfs-daemo
 5157 pablo     15   0 35372  10m 8708 S  0.0  2.1   0:00.63 nm-applet
 5171 pablo     15   0 17944 5756 4192 S  0.0  1.1   0:00.24 gnome-power-man
 5173 pablo     15   0 63504  13m 9132 S  0.0  2.6   0:00.90 trashapplet
 5188 pablo     16   0  2288  804  700 S  0.0  0.2   0:00.00 mapping-daemon
 5204 pablo     15   0 38208  11m 8696 S  0.0  2.3   0:00.92 mixer_applet2
 5206 pablo     16   0 19280  10m 7700 S  0.0  2.0   0:00.75 cpufreq-applet
 5208 pablo     16   0 18308 8536 7040 S  0.0  1.7   0:00.25 battstat-applet
 5215 pablo     16   0 23556  10m 7856 S  0.0  2.0   0:00.26 clock-applet
 5242 pablo     16   0 14772 2808 1864 S  0.0  0.5   0:01.48 gnome-screensav
 5246 dhcp      14  -2  2332  796  500 S  0.0  0.2   0:00.00 dhclient3
 5296 dhcp      15   0  2336 1136  832 S  0.0  0.2   0:00.00 dhclient
 5540 cupsys    26  10  4208 1900 1388 S  0.0  0.4   0:01.54 cupsd
 5771 pablo     15   0 34112 9.9m 6716 S  0.0  2.0   0:01.57 notification-da
 6165 syslog    26  10  1768  708  584 S  0.0  0.1   0:00.00 syslogd
 6936 pablo     18   0  2284  680  580 S  0.0  0.1   0:00.00 gnome-pty-helpe
 6937 pablo     16   0  5740 3376 1388 S  0.0  0.7   0:00.31 bash
 7361 pablo     15   0 49360  21m  12m S  0.0  4.2   0:02.93 gedit

---

