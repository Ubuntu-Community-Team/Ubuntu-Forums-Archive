---
title: "Ubuntu/xubuntu slower than should be on Inspiron 2200"
date: 2009-09-23
forum: Hardware
---

### Post by jtreach on 2009-09-23
Title says it all really the laptop isn't performing nearly as well as windows xp even after migrating from ubuntu to xubuntu.

Any ideas?

---

### Post by mikewhatever on 2009-09-23
Post your computer specs, the version of Ubuntu, and the output of **ps aux** from Terminal.

---

### Post by jtreach on 2009-09-23
Not sure of specifics (is there a command for that?):

# Processor: Intel Celeron M 1.40GHz/1.50GHz or Pentium M 725 (1.60GHz, 400MHZ FSB, 2MB Cache)
# Operating System: Xubuntu
# Memory: 256MB shared DDR SDRAM standard, Max Memory 1.28GB, 2 sockets of which one is user accessible
# Battery: standard 8-cell, 65WHr, 4:08 hours claimed battery life
# Dimensions: 1.46" x 13.0" x 10.6" (H x W x D)
# Weight: Starts at 5.99 lbs with 14.1" LCD and 8-cell battery
# Ports: 3 USB 2.0, 15-pin monitor out, 10/100 Ethernet, Modem, headphones, microphone, 1 PCMCIA slot
# Screen: 14.1" XGA 1024 x 768 or 15" XGA 1024 x 768
# Graphics: Integrated Intel Extreme 2 Graphics
# 30, 40 or 60GB hard drive (4200RPM)
# Optical Drive: DVD-ROM or CD Burner/DVD-ROM or CD/DVD Burner
# Wireless: Optional Dell 1350 (802.11 b/g) or Dell 1450 (802.11 a/b/g) wireless card

Xubuntu 9.04 is currently installed which is running marginally better than ubuntu 9.04 was but as I said above it's really not great.

Output of 'ps aux':

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3084   124 ?        Ss   18:50   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   18:50   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   18:50   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   18:50   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   18:50   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   18:50   0:02 [events/0]
root         7  0.0  0.0      0     0 ?        S<   18:50   0:00 [khelper]
root         8  0.0  0.0      0     0 ?        S<   18:50   0:00 [kstop/0]
root         9  0.0  0.0      0     0 ?        S<   18:50   0:00 [kintegrityd/0]
root        10  0.0  0.0      0     0 ?        S<   18:50   0:00 [kblockd/0]
root        11  0.0  0.0      0     0 ?        S<   18:50   0:00 [kacpid]
root        12  0.0  0.0      0     0 ?        S<   18:50   0:00 [kacpi_notify]
root        13  0.0  0.0      0     0 ?        S<   18:50   0:00 [cqueue]
root        14  0.0  0.0      0     0 ?        S<   18:50   0:02 [ata/0]
root        15  0.0  0.0      0     0 ?        S<   18:50   0:00 [ata_aux]
root        16  0.0  0.0      0     0 ?        S<   18:50   0:00 [ksuspend_usbd]
root        17  0.0  0.0      0     0 ?        S<   18:50   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   18:50   0:00 [kseriod]
root        19  0.0  0.0      0     0 ?        S<   18:50   0:00 [kmmcd]
root        20  0.0  0.0      0     0 ?        S<   18:50   0:00 [btaddconn]
root        21  0.0  0.0      0     0 ?        S<   18:50   0:00 [btdelconn]
root        24  0.0  0.0      0     0 ?        S<   18:50   0:03 [kswapd0]
root        25  0.0  0.0      0     0 ?        S<   18:50   0:00 [aio/0]
root        26  0.0  0.0      0     0 ?        S<   18:50   0:00 [ecryptfs-kthr]
root        29  0.0  0.0      0     0 ?        S<   18:50   0:03 [scsi_eh_0]
root        30  0.0  0.0      0     0 ?        S<   18:50   0:00 [scsi_eh_1]
root        31  0.0  0.0      0     0 ?        S<   18:50   0:00 [kstriped]
root        32  0.0  0.0      0     0 ?        S<   18:50   0:00 [kmpathd/0]
root        33  0.0  0.0      0     0 ?        S<   18:50   0:00 [kmpath_handle]
root        34  0.0  0.0      0     0 ?        S<   18:50   0:00 [ksnapd]
root        35  0.0  0.0      0     0 ?        S<   18:50   0:00 [kondemand/0]
root        36  0.0  0.0      0     0 ?        S<   18:50   0:00 [krfcommd]
root       692  0.0  0.0      0     0 ?        S<   18:50   0:01 [kjournald]
root       826  0.0  0.0   2224    72 ?        S<s  18:50   0:00 /sbin/udevd --d
root      1448  0.0  0.0      0     0 ?        S<   18:50   0:00 [kpsmoused]
root      1507  0.0  0.0      0     0 ?        S<   18:50   0:00 [pccardd]
root      1531  0.0  0.0      0     0 ?        S<   18:50   0:00 [b43]
root      2134  0.0  0.0   1808    76 tty4     Ss+  18:50   0:00 /sbin/getty 384
root      2135  0.0  0.0   1808    76 tty5     Ss+  18:50   0:00 /sbin/getty 384
root      2141  0.0  0.0   1808    76 tty2     Ss+  18:50   0:00 /sbin/getty 384
root      2143  0.0  0.0   1808    76 tty3     Ss+  18:50   0:00 /sbin/getty 384
root      2144  0.0  0.0   1808    76 tty6     Ss+  18:50   0:00 /sbin/getty 384
root      2208  0.0  0.0   2204    84 ?        Ss   18:50   0:00 /usr/sbin/acpid
syslog    2253  0.0  0.1   2040   260 ?        Ss   18:50   0:00 /sbin/syslogd -
root      2276  0.0  0.0   1968    96 ?        S    18:50   0:00 /bin/dd bs 1 if
klog      2278  0.0  0.0   3732   140 ?        Ss   18:50   0:00 /sbin/klogd -P
107       2301  0.0  0.3   3012   868 ?        Ss   18:50   0:02 /bin/dbus-daemo
root      2339  0.0  0.1  10600   272 ?        Ss   18:50   0:00 /usr/sbin/winbi
root      2347  0.0  0.1  10600   256 ?        S    18:50   0:00 /usr/sbin/winbi
110       2367  0.0  0.6   6448  1460 ?        Ss   18:50   0:06 /usr/sbin/hald
root      2370  0.0  0.5  16484  1372 ?        Ssl  18:50   0:00 /usr/sbin/conso
root      2433  0.0  0.2   3328   656 ?        S    18:50   0:02 hald-runner
root      2463  0.0  0.0   5176   212 ?        S    18:50   0:00 /usr/lib/hal/ha
root      2468  0.2  0.1   5204   464 ?        S    18:50   0:36 hald-addon-inpu
root      2524  0.0  0.1   5180   456 ?        S    18:50   0:03 hald-addon-stor
110       2527  0.0  0.0   5032   132 ?        S    18:50   0:00 hald-addon-acpi
root      2548  0.0  0.0   3556   188 ?        Ss   18:50   0:00 /usr/sbin/bluet
root      2581  0.0  0.0  15032   160 ?        Ss   18:50   0:00 /usr/sbin/gdm -
root      2584  0.0  0.1  15556   276 ?        S    18:50   0:00 /usr/sbin/gdm -
root      2588 14.7 15.1 118564 36840 tty7     Ds+  18:50  36:02 /usr/bin/X :0 -
root      2618  0.0  0.4  16432  1052 ?        Ssl  18:50   0:01 /usr/sbin/Netwo
root      2622  0.0  0.2   4284   500 ?        S    18:50   0:00 /sbin/wpa_suppl
root      2624  0.0  0.2   6932   696 ?        S    18:50   0:00 /usr/sbin/nm-sy
avahi     2646  0.0  0.1   2944   484 ?        Ss   18:50   0:00 avahi-daemon: r
avahi     2647  0.0  0.0   2944    48 ?        Ss   18:50   0:00 avahi-daemon: c
root      2674  0.0  0.1   6136   396 ?        Ss   18:50   0:00 /usr/sbin/cupsd
root      2694  0.0  0.1   4324   296 ?        Ss   18:50   0:00 /usr/bin/system
daemon    2767  0.0  0.0   2096    96 ?        Ss   18:50   0:00 /usr/sbin/atd
root      2795  0.0  0.0   3480   232 ?        Ss   18:50   0:00 /usr/sbin/cron
root      2894  0.0  0.0   1808    76 tty1     Ss+  18:50   0:00 /sbin/getty 384
root      2948  0.0  0.0   5176   216 ?        S    18:50   0:00 /usr/lib/hal/ha
root      2977  0.0  0.1   2276   340 ?        S    18:50   0:00 /sbin/dhclient
tom       2992  0.0  0.0   1872    76 ?        Ss   18:50   0:00 /bin/sh /etc/xd
tom       3124  0.0  0.0   4784   112 ?        Ss   18:50   0:00 /usr/bin/ssh-ag
tom       3127  0.0  0.0   3144   124 ?        S    18:50   0:00 /usr/bin/dbus-l
tom       3128  0.0  0.3   2936   796 ?        Ss   18:50   0:00 //bin/dbus-daem
tom       3138  0.0  0.8  25392  2180 ?        Sl   18:50   0:01 /usr/bin/xfce4-
tom       3169  0.0  0.2   3664   664 ?        S    18:50   0:00 /usr/lib/xfconf
tom       3171  0.0  0.5   6820  1276 ?        S    18:50   0:06 /usr/lib/libgco
tom       3180  0.0  0.6  15528  1484 ?        S    18:50   0:00 xfsettingsd
tom       3183  0.0  0.7  18712  1760 ?        S    18:50   0:00 Thunar --sm-cli
tom       3184  0.1  1.1  17636  2816 ?        Ss   18:50   0:17 gnome-screensav
tom       3186  0.0  0.1   3060   248 ?        S    18:50   0:00 /usr/lib/gamin/
tom       3187  0.0  1.3  69540  3380 ?        S    18:50   0:06 xfdesktop --dis
tom       3188  0.0  2.3  32128  5656 ?        S    18:50   0:09 xfce4-panel -r
tom       3190  0.0  0.8  18152  2064 ?        S    18:50   0:01 xfce4-settings-
tom       3192  0.0  0.9  38528  2308 ?        S    18:50   0:01 update-notifier
tom       3194  0.0  4.0  43948  9928 ?        Sl   18:50   0:12 /usr/lib/xfce4/
tom       3195  0.0  1.3  32868  3284 ?        S    18:50   0:01 /usr/lib/xfce4/
tom       3200  0.0  0.9  24792  2424 ?        Ss   18:50   0:00 gnome-power-man
tom       3202  0.0  0.0   1872    76 ?        Ss   18:50   0:00 /bin/sh /usr/bi
tom       3204  0.0  0.2   5752   560 ?        S    18:50   0:00 /usr/lib/gvfs/g
tom       3225  0.0  0.9  36912  2392 ?        Ss   18:50   0:01 nm-applet --sm-
tom       3234  0.0  0.1  16024   384 ?        Ts   18:50   0:00 bluetooth-apple
tom       3243  0.0  0.1  27728   380 ?        Ts   18:50   0:00 python /usr/sha
tom       3246  0.0  0.6  17708  1568 ?        S    18:50   0:00 /usr/lib/notifi
tom       3340  0.6  1.1  30560  2828 ?        S    18:50   1:31 /usr/bin/compiz
tom       3395  0.0  1.0  32900  2484 ?        Sl   18:50   0:00 /usr/lib/xfce4/
tom       3427  0.0  0.9  27468  2352 ?        S    18:50   0:00 /usr/lib/thunar
tom       3434  0.0  0.0   1872    72 ?        Ss   18:51   0:00 /bin/sh -c /usr
tom       3435  0.0  0.0   1872    76 ?        S    18:51   0:00 /bin/sh /usr/bi
tom       3437  0.1  2.3  34196  5628 ?        S    18:51   0:17 /usr/bin/emeral
tom       4591  0.0  0.3   7988   804 ?        S    19:07   0:00 /usr/lib/gvfs/g
tom       4593  0.0  0.2   8360   652 ?        S    19:07   0:00 /usr/lib/gvfs/g
root      5415  0.0  0.0  21756   132 ?        S    19:18   0:01 apt-get install
root      5481  0.0  0.0  26728   120 pts/1    Ss+  19:19   0:00 /usr/bin/dpkg -
root      5504  0.0  0.0  11228   124 pts/1    S+   19:19   0:00 /usr/bin/perl -
root      5511  0.0  0.0   1872    80 pts/1    S+   19:19   0:00 /bin/sh -e /var
root      5517  0.0  0.0   4976    80 pts/1    S+   19:19   0:00 whiptail --back
root     10406  0.0  0.0      0     0 ?        S    20:32   0:00 [pdflush]
tom      15650 13.4 37.7 301500 91572 ?        Sl   21:58   7:38 /usr/lib/firefo
tom      16276  0.0  2.1  56572  5260 ?        Ss   22:02   0:01 /usr/bin/python
root     16441  0.0  0.0      0     0 ?        S    22:05   0:00 [pdflush]
tom      19069  1.8  5.6  30908 13588 ?        Ss   22:54   0:00 xfce4-terminal
tom      19074  0.0  0.2   2036   700 ?        S    22:54   0:00 gnome-pty-helpe
tom      19075  1.5  1.2   5824  3096 pts/2    Ss   22:54   0:00 bash
root     19092  0.0  0.0      0     0 ?        S    22:54   0:00 [pdflush]
tom      19101  0.0  0.4   2768  1040 pts/2    R+   22:55   0:00 ps aux

```

Thanks for the help by the way, much appreciated.

---

### Post by snowpine on 2009-09-23
Your processor is not too bad, but you need more ram. 256mb is borderline for any modern operating system (Windows XP is 8 years old and has lower system requirements).

---

### Post by mikewhatever on 2009-09-23
Thanks for the info. I don't quite understand the amount of RAM available. Is 1.28GB the amount of RAM+swap? As snowpine said, 256MB of RAM is not a lot, consider adding some if you can. The only two processes that seem to eat up resources are XORG and Firefox. Turning off compiz might lighten things up, and in addition to that, disable the startup programs you don't need under System->Admin->Startup Programs to free some of the RAM. 
Possible candidates are:
Bluetooth manager
Hardware Drivers
Remote Desktop
User Folder Update
Visual Assistance
Print Queue Applet
Update Notifier

---

