---
title: "Sound card issue?  Linux newbie"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by kmike82 on 2008-02-05
Hey everyone!  Linux newbie here.

When I run any multimedia program, I lose sound in all of my other programs.  Example:  If I'm running rhythmbox, the sounds in Pidgin disappear.  I think this is causing Pidgin to crash (only crashes while I'm listening to mp3s).

I'm using the onboard sound on an ECS K7s5a mobo.

Is this a hardware problem?  Am I in the wrong place?  

Any ideas on a solution?

---

### Post by kmike82 on 2008-02-05
bump.

thanks in advance

---

### Post by Cannaregio on 2008-02-05
The following is a great general fixall for sound issues and could (underlined= *could)* work:
first check if you really have more than one card...

```
asoundconf list
```

...then repair your sound...

```
asoundconf reset-default-card
```


Also: do you have the "another program is blocking the soundcard" error?

...then...
```
ps au
```

...in order to check who's responsible, say "PID 32382", and then kill it with...

```
sudo kill -9 32382
```

---

### Post by kmike82 on 2008-02-05
Thanks for the reply.  The problem still seems to be there.

There doesnt seem to be anything out of the ordinary when i type  "ps au" and there isnt anything of note in '/var/log/messages'

---

### Post by Cannaregio on 2008-02-08
Sorry, forgot the sudo, try again with
```
sudo ps aux
```

---

### Post by kmike82 on 2008-02-08
I tried the 'sudo ps aux', I'm not sure what I'm looking for.  Theres a lot of stuff in there

I wish i could format this better but here is what comes up

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2952  1856 ?        Ss   Feb07   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Feb07   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   Feb07   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Feb07   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Feb07   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Feb07   0:00 [khelper]
root        26  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kblockd/0]
root        41  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kseriod]
root        81  0.0  0.0      0     0 ?        S    Feb07   0:00 [pdflush]
root        82  0.0  0.0      0     0 ?        S    Feb07   0:00 [pdflush]
root        83  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kswapd0]
root       134  0.0  0.0      0     0 ?        S<   Feb07   0:00 [aio/0]
root      1906  0.0  0.0      0     0 ?        S<   Feb07   0:00 [khpsbpkt]
root      1908  0.0  0.0      0     0 ?        S<   Feb07   0:00 [knodemgrd_0]
root      1911  0.0  0.0      0     0 ?        S<   Feb07   0:00 [ata/0]
root      1912  0.0  0.0      0     0 ?        S<   Feb07   0:00 [ata_aux]
root      1914  0.0  0.0      0     0 ?        S<   Feb07   0:00 [scsi_eh_0]
root      1915  0.0  0.0      0     0 ?        S<   Feb07   0:00 [scsi_eh_1]
root      1920  0.0  0.0      0     0 ?        S<   Feb07   0:00 [ksuspend_usbd]
root      1921  0.0  0.0      0     0 ?        S<   Feb07   0:00 [khubd]
root      2410  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kjournald]
root      2613  0.0  0.1   3020  1368 ?        S<s  Feb07   0:00 /sbin/udevd --daemon
root      3537  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kpsmoused]
root      3662  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kgameportd]
root      3897  0.0  0.0   3788   952 ?        Ss   Feb07   0:00 /sbin/mount.ntfs /dev/hda1 /media/hda1 -o rw,umask=007,gid=46
root      3900  0.0  0.1   4164  1440 ?        Ss   Feb07   0:02 /sbin/mount.ntfs /dev/hda5 /media/hda5 -o rw,umask=007,gid=46
root      4155  0.0  0.0   1692   516 tty4     Ss+  Feb07   0:00 /sbin/getty 38400 tty4
root      4156  0.0  0.0   1696   516 tty5     Ss+  Feb07   0:00 /sbin/getty 38400 tty5
root      4160  0.0  0.0   1692   512 tty2     Ss+  Feb07   0:00 /sbin/getty 38400 tty2
root      4161  0.0  0.0   1696   520 tty3     Ss+  Feb07   0:00 /sbin/getty 38400 tty3
root      4162  0.0  0.0   1696   520 tty1     Ss+  Feb07   0:00 /sbin/getty 38400 tty1
root      4163  0.0  0.0   1696   520 tty6     Ss+  Feb07   0:00 /sbin/getty 38400 tty6
root      4234  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kondemand/0]
syslog    4302  0.0  0.0   1916   736 ?        Ss   Feb07   0:00 /sbin/syslogd -u syslog
root      4359  0.0  0.0   1836   536 ?        S    Feb07   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4361  0.0  0.1   2596  1396 ?        Ss   Feb07   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4382  0.0  0.1   3156  1304 ?        Ss   Feb07   0:01 /usr/bin/dbus-daemon --system
root      4398  0.0  0.2  28948  2164 ?        Ssl  Feb07   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4412  0.0  0.1   3276  1276 ?        Ss   Feb07   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManage
root      4425  0.0  0.0   3088   816 ?        Ss   Feb07   0:00 /usr/bin/system-tools-backends
root      4426  0.0  0.1   2772  1256 ?        S    Feb07   0:00 dbus-daemon --session --print-address --nofork
107       4445  0.0  0.3   5760  3784 ?        Ss   Feb07   0:00 /usr/sbin/hald
root      4446  0.0  0.0   3096  1020 ?        S    Feb07   0:00 hald-runner
107       4496  0.0  0.0   2160   896 ?        S    Feb07   0:00 hald-addon-keyboard: listening on /dev/input/event1
root      4534  0.0  0.2  30500  2704 ?        Ssl  Feb07   0:00 /usr/sbin/cupsd
root      4561  0.0  0.0      0     0 ?        S<   Feb07   0:00 [kapmd]
root      4575  0.0  0.0   1696   472 ?        Ss   Feb07   0:00 /usr/sbin/apmd -P /etc/apm/apmd_proxy --proxy-timeout 30
107       4600  0.0  0.1   3260  1188 ?        S    Feb07   0:00 hald-addon-storage: polling /dev/hdc (every 2 sec)
107       4604  0.0  0.1   3260  1184 ?        S    Feb07   0:10 hald-addon-storage: polling /dev/hdd (every 2 sec)
root      5050  0.0  0.2   7568  2140 ?        Ssl  Feb07   0:00 /usr/sbin/console-kit-daemon
avahi     5135  0.0  0.1   2728  1412 ?        Ss   Feb07   0:00 avahi-daemon: registering [kmike82.local]
avahi     5136  0.0  0.0   2728   452 ?        Ss   Feb07   0:00 avahi-daemon: chroot helper
root      5150  0.0  0.0   1992   904 ?        Ss   Feb07   0:00 /usr/sbin/dhcdbd --system
root      5170  0.0  0.1   2920  1180 ?        Ss   Feb07   0:00 /usr/sbin/hcid -x -s
root      5180  0.0  0.1   2840  1212 ?        S    Feb07   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5181  0.0  0.0   2768   972 ?        S    Feb07   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5189  0.0  0.0      0     0 ?        S<   Feb07   0:00 [krfcommd]
root      5219  0.0  0.1  13100  1620 ?        Ss   Feb07   0:00 /usr/sbin/gdm
ntp       5254  0.0  0.1   4132  1252 ?        Ss   Feb07   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 109:120 -g
daemon    5290  0.0  0.0   1960   428 ?        Ss   Feb07   0:00 /usr/sbin/atd
root      5305  0.0  0.0   2332   908 ?        Ss   Feb07   0:00 /usr/sbin/cron
kmike82   5464  0.0  0.1   2904  1052 ?        Ss   Feb07   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
kmike82   5498  0.0  0.3   8724  3456 ?        S    Feb07   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
kmike82   5630  0.0  0.8  28064  8508 ?        RNl  Feb07   0:04 trackerd
root      5678  0.0  0.1   3852  1572 ?        S    Feb07   0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global3
dhcp      5714  0.0  0.1   2416  1172 ?        S    Feb07   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.ath0.leases -pf /var/run/dhclient.ath
root      5730  0.0  0.2  13548  2884 ?        S    Feb07   0:00 /usr/sbin/gdm
kmike82   5736  0.0  0.3   6820  4096 ?        S    Feb07   0:02 /usr/lib/libgconf2-4/gconfd-2 11
root      5748  7.1  4.5  53348 46920 tty7     SLs+ Feb07  74:54 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
kmike82   5819  0.0  0.1  13268  1732 ?        SL   Feb07   0:00 /usr/bin/gnome-keyring-daemon -d
kmike82   5822  0.0  0.7  27688  7388 ?        Ssl  Feb07   0:00 /usr/bin/gnome-session
kmike82   5858  0.0  0.0   4432   540 ?        Ss   Feb07   0:00 /usr/bin/ssh-agent /usr/bin/gnome-session
kmike82   5862  0.0  0.1   2908  1168 ?        Ss   Feb07   0:02 dbus-daemon --fork --print-address 17 --print-pid 19 --session
kmike82   5864  0.0  1.0  38624 10360 ?        Sl   Feb07   0:03 /usr/lib/gnome-control-center/gnome-settings-daemon
kmike82   5871  0.0  0.3  39916  3164 ?        Ssl  Feb07   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=1
kmike82   5879  0.0  2.4  88712 25404 ?        S    Feb07   0:25 gnome-panel --sm-client-id default1
kmike82   5881  0.0  0.5  16288  5728 ?        S    Feb07   0:02 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf
kmike82   5882  0.0  3.0  90932 31688 ?        S    Feb07   0:11 nautilus --no-default-window --sm-client-id default2
kmike82   5915  0.0  0.5  17068  5944 ?        Ss   Feb07   0:28 gnome-screensaver
kmike82   5917  0.0  0.3   8720  3436 ?        S    Feb07   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
kmike82   5918  0.0  0.4  19592  5148 ?        Ss   Feb07   0:00 gnome-volume-manager --sm-client-id default4
kmike82   5927  0.0  0.9  65948  9868 ?        S    Feb07   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApple
kmike82   5940  0.0  1.4  37184 14716 ?        S    Feb07   0:03 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID:GNOME_StickyNot
kmike82   5958  0.0  0.0   2660   896 ?        S    Feb07   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
kmike82   5964  0.0  3.2  81924 34056 ?        Sl   Feb07   0:02 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:De
kmike82   5975  0.0  1.3  77604 13640 ?        S    Feb07   0:01 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherAp
kmike82   5978  0.0  0.6  90668  6788 ?        Sl   Feb07   0:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-activate-iid=OAFIID:GNOME_Evolu
kmike82   5989  0.0  1.3  45384 13804 ?        Sl   Feb07   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Fa
kmike82   5991  0.0  1.1  35400 12144 ?        S    Feb07   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:
kmike82   6022  0.0  1.0  19088 11188 ?        S    Feb07   0:10 /usr/bin/emerald --replace
kmike82   6024  0.0  0.6  19336  6884 ?        S    Feb07   0:00 vino-session --sm-client-id default5
kmike82   6025  0.0  0.5  13280  5440 ?        S    Feb07   0:00 bluetooth-applet
kmike82   6029  0.0  1.3  39028 14460 ?        S    Feb07   0:00 update-notifier
kmike82   6039  0.0  1.1  44504 11704 ?        S    Feb07   0:00 nm-applet --sm-disable
kmike82   6040  0.0  1.7  28084 17764 ?        S    Feb07   0:22 python /usr/share/system-config-printer/applet.py
kmike82   6048  0.0  0.7  22464  8096 ?        Ss   Feb07   0:00 gnome-power-manager
kmike82   6072  0.0  3.9 150400 40804 ?        Sl   Feb07   0:55 pidgin
kmike82   6074  0.0  3.4  67928 35816 ?        Sl   Feb07   0:10 /usr/bin/perl -w /usr/bin/checkgmail
kmike82   6088  0.0  0.0   1752   524 ?        S    Feb07   0:00 /bin/sh /usr/bin/firefox
kmike82   6100  0.0  0.0   1752   528 ?        S    Feb07   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
kmike82   6104  4.9 13.6 317488 141120 ?       Sl   Feb07  51:44 /usr/lib/firefox/firefox-bin
kmike82   6199  0.0  1.1  33988 11704 ?        S    Feb07   0:02 /usr/lib/notification-daemon/notification-daemon
kmike82   6758  0.0  1.2  15060 12540 ?        Ss   Feb07   0:12 /home/kmike82/cxoffice/bin/../lib/../bin/wineserver
kmike82   6760  0.0  1.4 2790120 15152 ?       SLsl Feb07   0:00 c:\windows\system32\explorer.exe /desktop                                         
kmike82   6789  0.0  1.5 2791896 15712 ?       SL   Feb07   0:00 winewrapper.exe cxoffice --wait-children --start -- c:/windows/profiles/All Users/S
kmike82   6791  0.0  1.6 2794084 17084 ?       RL   Feb07   0:11 C:\Program Files\Alarm Clock\Alarm Clock.exe                                      
kmike82   6812  0.0  1.5  49832 16132 ?        S    Feb07   0:22 metacity --replace
kmike82   7481  0.0  1.9  64736 19976 ?        Sl   01:14   0:01 gnome-terminal
kmike82   7486  0.0  0.0   2664   740 ?        S    01:14   0:00 gnome-pty-helper
kmike82   7487  0.0  0.3   5784  3176 pts/0    Ss+  01:14   0:00 bash
kmike82  10344  0.2  0.3   5784  3176 pts/1    Ss   15:27   0:00 bash
kmike82  10374 24.2  3.6 171064 37348 ?        Sl   15:28   0:05 rhythmbox
root     10405  0.0  0.0   2620  1000 pts/1    R+   15:28   0:00 ps aux

---

### Post by Cannaregio on 2008-02-13
Reduce to your non root stuff  using ```
top
``` and then ```
u
``` for user and then ```
kmike
``` for yourself. Kill with ```
k
``` and code 9 every PID that could be interfering with your card.
Good luck.

---

