---
title: "What is keeping my disk drive from spinning down?"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Strid on 2007-10-02
I'm running two harddrives in my computer and would like them both to spin down when I'm not using the computer.

If I do like this: ```
sudo hdparm - S 1 /dev/<name of drive>
```

both drives should then spin down after 5 secs (because I did it with both /dev/sda and sdb :))

It works with sdb, which is a drive only containing things like music, documents, movies, etc. so naturally, nothing should be read from that drive when the computer is ideling.

WIth my other drive /dev/sda, which contains a Ubuntu partition, swap, a Windows NTFS and a FAT32 partition, it will never spin down. Every about two seconds I hear activity from the drive, so naturally it won't shut it self down. So my question is, what could be the culprit that wants to read from the drive (It's a Raptor, so it's quite noisy too)?

If I do a "ps aux > psaux.txt" that would tell me everything that is going on, right? Well the output is here, if anyone could identify anything suspicious.

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2908  1904 ?        Ss   10:23   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:23   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   10:23   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    10:23   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S    10:23   0:00 [migration/1]
root         6  0.0  0.0      0     0 ?        SN   10:23   0:00 [ksoftirqd/1]
root         7  0.0  0.0      0     0 ?        S    10:23   0:00 [watchdog/1]
root         8  0.0  0.0      0     0 ?        S<   10:23   0:00 [events/0]
root         9  0.0  0.0      0     0 ?        S<   10:23   0:00 [events/1]
root        10  0.0  0.0      0     0 ?        S<   10:23   0:00 [khelper]
root        11  0.0  0.0      0     0 ?        S<   10:23   0:00 [kthread]
root        35  0.0  0.0      0     0 ?        S<   10:23   0:00 [kblockd/0]
root        36  0.0  0.0      0     0 ?        S<   10:23   0:00 [kblockd/1]
root        37  0.0  0.0      0     0 ?        S<   10:23   0:00 [kacpid]
root        38  0.0  0.0      0     0 ?        S<   10:23   0:00 [kacpi_notify]
root       167  0.0  0.0      0     0 ?        S<   10:23   0:00 [kseriod]
root       196  0.0  0.0      0     0 ?        S    10:23   0:00 [pdflush]
root       197  0.0  0.0      0     0 ?        S    10:23   0:00 [pdflush]
root       198  0.0  0.0      0     0 ?        S<   10:23   0:00 [kswapd0]
root       199  0.0  0.0      0     0 ?        S<   10:23   0:00 [aio/0]
root       200  0.0  0.0      0     0 ?        S<   10:23   0:00 [aio/1]
root       830  0.0  0.0      0     0 ?        S    10:23   0:00 [kirqd]
root      2107  0.0  0.0      0     0 ?        S<   10:23   0:00 [ksuspend_usbd]
root      2109  0.0  0.0      0     0 ?        S<   10:23   0:00 [khubd]
root      2129  0.0  0.0      0     0 ?        S<   10:23   0:00 [ata/0]
root      2130  0.0  0.0      0     0 ?        S<   10:23   0:00 [ata/1]
root      2131  0.0  0.0      0     0 ?        S<   10:23   0:00 [ata_aux]
root      2210  0.0  0.0      0     0 ?        S<   10:23   0:00 [scsi_eh_0]
root      2211  0.0  0.0      0     0 ?        S<   10:23   0:00 [scsi_eh_1]
root      2421  0.0  0.0      0     0 ?        S<   10:23   0:00 [kjournald]
root      2620  0.0  0.0   2896  1236 ?        S<s  10:23   0:00 /sbin/udevd --daemon
root      3556  0.0  0.0      0     0 ?        S<   10:23   0:00 [kpsmoused]
root      3591  0.0  0.0      0     0 ?        S<   10:23   0:00 [kgameportd]
root      4410  0.0  0.0   1648   508 tty4     Ss+  10:23   0:00 /sbin/getty 38400 tty4
root      4411  0.0  0.0   1648   504 tty5     Ss+  10:23   0:00 /sbin/getty 38400 tty5
root      4413  0.0  0.0   2752  1204 tty2     Ss   10:23   0:00 /bin/login --       
root      4417  0.0  0.0   2756  1204 tty1     Ss   10:23   0:00 /bin/login --       
root      4418  0.0  0.0   1648   504 tty6     Ss+  10:23   0:00 /sbin/getty 38400 tty6
root      4678  0.0  0.0   2256  1172 ?        Ss   10:23   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4792  0.0  0.0   1700   660 ?        Ss   10:23   0:00 /sbin/syslogd
root      4848  0.0  0.0   1792   524 ?        Ss   10:23   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4850  0.0  0.0   2552  1368 ?        Ss   10:23   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4871  0.0  0.0   2844  1076 ?        Ss   10:23   0:00 /usr/bin/dbus-daemon --system
107       4887  0.0  0.1   5476  3764 ?        Ss   10:23   0:00 /usr/sbin/hald
root      4888  0.0  0.0   2876  1016 ?        S    10:23   0:00 hald-runner
107       4894  0.0  0.0   2108   904 ?        S    10:23   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       4895  0.0  0.0   2112   900 ?        S    10:23   0:00 hald-addon-keyboard: listening on /dev/input/event4
107       4896  0.0  0.0   2108   896 ?        S    10:23   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       4899  0.0  0.0   2112   888 ?        S    10:23   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4925  0.0  0.0   1940   888 ?        Ss   10:23   0:00 /usr/sbin/dhcdbd --system
root      4940  0.0  0.0  20532  1996 ?        Ssl  10:23   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     4957  0.0  0.0   2804  1404 ?        Ss   10:23   0:00 avahi-daemon: registering [fx60.local]
avahi     4958  0.0  0.0   2672   464 ?        Ss   10:23   0:00 avahi-daemon: chroot helper
root      4971  0.0  0.0   3056  1268 ?        Ss   10:23   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4985  0.0  0.0   2868   800 ?        Ss   10:23   0:00 /usr/bin/system-tools-backends
root      4986  0.0  0.0   2720  1220 ?        S    10:23   0:00 dbus-daemon --session --print-address --nofork
root      5014  0.0  0.0  12216  1408 ?        Ss   10:23   0:00 /usr/sbin/gdm
root      5016  0.0  0.1  12584  2388 ?        S    10:23   0:00 /usr/sbin/gdm
root      5036  1.5  3.9  87032 82632 tty7     SLs+ 10:23   7:18 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5105  0.0  0.0   6416   836 ?        Ss   10:23   0:00 /usr/sbin/hpiod
hplip     5111  0.0  0.2   9988  4892 ?        S    10:23   0:00 python /usr/sbin/hpssd
dhcp      5144  0.0  0.0   2456  1216 ?        S    10:23   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
root      5224  0.0  0.0   1920   736 ?        S    10:23   0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sda /dev/sdb
root      5291  0.0  0.0   2696   996 ?        Ss   10:23   0:00 /usr/sbin/hcid -x -s
root      5313  0.0  0.0      0     0 ?        S<   10:23   0:00 [krfcommd]
proftpd   5335  0.0  0.0   9276  1552 ?        Ss   10:23   0:00 proftpd: (accepting connections)
daemon    5368  0.0  0.0   1908   420 ?        Ss   10:23   0:00 /usr/sbin/atd
root      5382  0.0  0.0   2280   900 ?        Ss   10:23   0:00 /usr/sbin/cron
anders    5485  0.0  0.5  30268 11128 ?        Ssl  10:23   0:00 x-session-manager
anders    5523  0.0  0.0   4256   528 ?        Ss   10:23   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
anders    5526  0.0  0.0   2660   632 ?        S    10:23   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
anders    5527  0.0  0.0   2848  1024 ?        Ss   10:23   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
anders    5529  0.0  0.1   6572  4076 ?        S    10:23   0:00 /usr/lib/libgconf2-4/gconfd-2 6
anders    5532  0.0  0.0   2760  1000 ?        S    10:23   0:00 /usr/bin/gnome-keyring-daemon
anders    5534  0.0  0.4  29716 10000 ?        Sl   10:23   0:03 /usr/lib/control-center/gnome-settings-daemon
anders    5563  0.0  0.0   1716   480 ?        Ss   10:23   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
anders    5564  0.0  0.1   4820  3020 ?        S    10:23   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
anders    5568  0.0  0.5  17516 10696 ?        S    10:23   0:14 /usr/bin/metacity --sm-client-id=default0
anders    5573  0.0  0.9  42540 20400 ?        S    10:23   0:15 gnome-panel --sm-client-id default1
anders    5590  0.0  1.4  83360 30168 ?        S    10:23   0:04 nautilus --no-default-window --sm-client-id default2
anders    5596  0.0  0.1  39564  3044 ?        Ssl  10:23   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
anders    5605  0.0  0.2  18912  4944 ?        Ss   10:23   0:00 gnome-volume-manager --sm-client-id default4
anders    5608  0.0  0.1   8476  3412 ?        S    10:23   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
anders    5612  0.0  0.5  31184 12024 ?        S    10:23   0:00 update-notifier
anders    5616  0.0  0.5  30856 12144 ?        S    10:23   0:00 nm-applet --sm-disable
104       5627  0.0  0.0   1896   756 ?        S<s  10:23   0:00 avahi-autoipd: [eth1] bound 169.254.7.158
root      5628  0.0  0.0   1684   352 ?        S<s  10:23   0:00 avahi-autoipd: [eth1] callout dispatcher
anders    5629  0.0  0.3  40008  8192 ?        Sl   10:23   0:00 gnome-cups-icon --sm-client-id default3
anders    5630  0.0  0.2  28536  5764 ?        Ss   10:23   0:00 gnome-power-manager
anders    5638  0.0  0.6  67900 14464 ?        S    10:23   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
anders    5651  0.0  0.0   2456   884 ?        S    10:23   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
anders    5682  0.0  0.6  32464 12800 ?        S    10:23   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
anders    5690  0.0  0.1   5544  3028 tty1     S    10:23   0:00 -bash
anders    5706  0.0  0.1   4620  2352 tty1     S+   10:23   0:00 ssh -Tl nykp21 fw1.k-net.dk
dhcp      5707  0.0  0.0   2448   780 ?        S<s  10:23   0:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
anders    5755  0.0  0.2  16072  4320 ?        Ss   10:24   0:12 gnome-screensaver
cupsys    5999  0.0  0.0   4676  1936 ?        SNs  10:28   0:00 /usr/sbin/cupsd
anders   20986  0.0  0.1   5580  3088 tty2     S    18:14   0:00 -bash
root     21107  0.0  0.0   1648   508 tty3     Ss+  18:17   0:00 /sbin/getty 38400 tty3
anders   21253  0.0  0.0   2560   992 tty2     R+   18:21   0:00 ps aux

```

Hope anyone has an answer, that'd be great!! :popcorn: (Nice smilies, btw)

---

### Post by Strid on 2007-10-10
Anyone got an idea?

---

### Post by just-want-one-attachment on 2008-01-25
This will be difficult for you...

First off, as you can see with ps, there are tonnes of processes doing tonnes of different things at the same time.  Any of these could be writing logs, backup info, and your kernel could at anytime be writing aged memory bits to swap.

That said, look at strace.  ex; strace -p pid -p pid -p pid  -e trace=open,close,read,write

This will track many processes whenever they access the disk...

You can forget tracing anything in brackets [] because those are parts of the kernel...

Just for fun i turned off klogd syslogd and swap:
sudo /etc/init.d/klogd stop
sudo /etc/init.d/sysklogd stop
sudo swapoff -a

While it improved things there is still something else writing.  

2 points:

You may want to do the above _and_ logout to see if it is some gnome process that is writing to the disk.
Strace write reports AND disk activity will probably not happen at the same time.  Writes/reads can be buffered to memory and changes only go to disk after a while.

cheers,
jake

p.s. Do a 'man lsof' too... it's a good tool

---

