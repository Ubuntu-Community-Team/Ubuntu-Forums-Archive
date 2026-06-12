---
title: "Stopping internet access"
date: 2008-07-17
forum: General Help
---

### Post by Tifie on 2008-07-17
Hi, I'm quite new to Ubuntu. My problem is that every few seconds something keeps trying to access the internet, even when I disable the network connection. I was wondering if there is a way to stop it.

I recently installed Apache2, MySQL and PHP so I could test my website locally before publishing updates. At the risk of sounding dense, I think that this has something to do with my problem.

After googling for awhile I found how to use the netstat command but that didn't tell me any program info. When I ran it with sudo it didn't give any information at all. One thing it does tell me is that the program is contacting sites like canonical.com and "Tumbleweed Valicert Validation Authority", whatever that is.

Below is the output of netstat -utp. Can someone help?

```
user@computer:~$ netstat -utp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 xxx.xxx.xxx.xxx:50316      64.74.243.37:www        TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:53125      91.189.94.12:www        TIME_WAIT   -               
tcp        0      1 xxx.xxx.xxx.xxx:53531      64.191.203.30:www       FIN_WAIT1   -               
tcp        0      0 xxx.xxx.xxx.xxx:47421      68.178.232.183:www      TIME_WAIT   -               
tcp        0      1 xxx.xxx.xxx.xxx:42484      66.102.9.127:www        FIN_WAIT1   -               
tcp        0      1 xxx.xxx.xxx.xxx:53524      64.191.203.30:www       FIN_WAIT1   -               
tcp        1      1 xxx.xxx.xxx.xxx:56707      69.25.138.122:www       LAST_ACK    -               
tcp        0      0 xxx.xxx.xxx.xxx:53123      91.189.94.12:www        TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:53121      91.189.94.12:www        TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:48979      68.178.232.168:www      TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:42483      66.102.9.127:www        TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:48995      68.178.232.168:www      TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:40801      66.102.9.99:www         TIME_WAIT   -               
tcp        0      1 xxx.xxx.xxx.xxx:47257      66.102.9.104:www        FIN_WAIT1   -               
tcp        0      0 xxx.xxx.xxx.xxx:50307      64.74.243.37:www        TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:53533      64.191.203.30:www       TIME_WAIT   -               
tcp        0      0 xxx.xxx.xxx.xxx:53122      91.189.94.12:www        TIME_WAIT   -               

```

---

### Post by nikgare on 2008-07-18
What programs do you have running  - also programs in the systray?
I have skype running here and that access the net every second or so.
You could also try running ***sudo* netstat -utp**

---

### Post by jimv on 2008-07-18
I'm curious has to how you know that something is trying to access the internet?

---

### Post by Tifie on 2008-07-18
Thanks for the replies. nikgare, I have nothing in the system tray, apart from the network and volume controls. Here's a list of all the programs I have running:

```
user@computer:~$ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 14:18 ?        00:00:01 /sbin/init
root         2     0  0 14:18 ?        00:00:00 [kthreadd]
root         3     2  0 14:18 ?        00:00:00 [migration/0]
root         4     2  0 14:18 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 14:18 ?        00:00:00 [watchdog/0]
root         6     2  0 14:18 ?        00:00:00 [migration/1]
root         7     2  0 14:18 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 14:18 ?        00:00:00 [watchdog/1]
root         9     2  0 14:18 ?        00:00:00 [events/0]
root        10     2  0 14:18 ?        00:00:00 [events/1]
root        11     2  0 14:18 ?        00:00:00 [khelper]
root        46     2  0 14:18 ?        00:00:00 [kblockd/0]
root        47     2  0 14:18 ?        00:00:00 [kblockd/1]
root        50     2  0 14:18 ?        00:00:00 [kacpid]
root        51     2  0 14:18 ?        00:00:00 [kacpi_notify]
root       129     2  0 14:18 ?        00:00:00 [kseriod]
root       172     2  0 14:18 ?        00:00:00 [pdflush]
root       173     2  0 14:18 ?        00:00:00 [kswapd0]
root       214     2  0 14:18 ?        00:00:00 [aio/0]
root       215     2  0 14:18 ?        00:00:00 [aio/1]
root      1065     2  0 14:18 ?        00:00:00 [ata/0]
root      1066     2  0 14:18 ?        00:00:00 [ata/1]
root      1067     2  0 14:18 ?        00:00:00 [ata_aux]
root      1072     2  0 14:18 ?        00:00:00 [scsi_eh_0]
root      1074     2  0 14:18 ?        00:00:00 [scsi_eh_1]
root      1080     2  0 14:18 ?        00:00:00 [scsi_eh_2]
root      1082     2  0 14:18 ?        00:00:00 [scsi_eh_3]
root      1477     2  0 14:18 ?        00:00:00 [ksuspend_usbd]
root      1480     2  0 14:18 ?        00:00:00 [khubd]
root      2524     1  1 14:18 ?        00:00:12 /sbin/mount.ntfs /dev/disk/by-uu
root      2560     2  0 14:18 ?        00:00:00 [loop0]
root      2562     2  0 14:18 ?        00:00:00 [kjournald]
root      2781     1  0 14:19 ?        00:00:00 /sbin/udevd --daemon
root      3260     2  0 14:19 ?        00:00:00 [kpsmoused]
root      3850     2  0 14:19 ?        00:00:00 [scsi_eh_4]
root      3851     2  0 14:19 ?        00:00:00 [usb-storage]
root      4661     1  0 14:19 tty4     00:00:00 /sbin/getty 38400 tty4
root      4662     1  0 14:19 tty5     00:00:00 /sbin/getty 38400 tty5
root      4668     1  0 14:19 tty2     00:00:00 /sbin/getty 38400 tty2
root      4669     1  0 14:19 tty3     00:00:00 /sbin/getty 38400 tty3
root      4670     1  0 14:19 tty6     00:00:00 /sbin/getty 38400 tty6
root      4848     1  0 14:19 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4904     2  0 14:19 ?        00:00:00 [kondemand/0]
root      4905     2  0 14:19 ?        00:00:00 [kondemand/1]
syslog    4969     1  0 14:19 ?        00:00:00 /sbin/syslogd -u syslog
root      5024     1  0 14:19 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      5026     1  0 14:19 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
108       5048     1  0 14:19 ?        00:00:00 /usr/bin/dbus-daemon --system
root      5064     1  0 14:19 ?        00:00:00 /usr/sbin/NetworkManager --pid-f
root      5078     1  0 14:19 ?        00:00:00 /usr/sbin/NetworkManagerDispatch
root      5091     1  0 14:19 ?        00:00:00 /usr/bin/system-tools-backends
avahi     5120     1  0 14:19 ?        00:00:00 avahi-daemon: running [computer.l
avahi     5121  5120  0 14:19 ?        00:00:00 avahi-daemon: chroot helper
root      5172     1  0 14:19 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5214  5172  0 14:19 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr
root      5215  5172  0 14:19 ?        00:00:00 logger -p daemon.err -t mysqld_s
root      5300     1  0 14:19 ?        00:00:00 /usr/sbin/atieventsd
root      5328     1  0 14:19 ?        00:00:00 /usr/sbin/cupsd
root      5386     1  0 14:19 ?        00:00:00 /usr/sbin/nmbd -D
root      5388     1  0 14:19 ?        00:00:00 /usr/sbin/smbd -D
root      5405  5388  0 14:19 ?        00:00:00 /usr/sbin/smbd -D
root      5406     1  0 14:19 ?        00:00:00 /usr/sbin/winbindd
root      5450  5406  0 14:19 ?        00:00:00 /usr/sbin/winbindd
root      5451     1  0 14:19 ?        00:00:00 /usr/sbin/dhcdbd --system
111       5470     1  0 14:19 ?        00:00:00 /usr/sbin/hald
root      5473     1  0 14:19 ?        00:00:00 /usr/sbin/console-kit-daemon
root      5474  5470  0 14:19 ?        00:00:00 hald-runner
root      5548  5474  0 14:19 ?        00:00:00 hald-addon-input: Listening on /
root      5567  5474  0 14:19 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
111       5568  5474  0 14:19 ?        00:00:00 hald-addon-acpi: listening on ac
root      5577  5474  0 14:19 ?        00:00:00 hald-addon-storage: polling /dev
root      5579  5474  0 14:19 ?        00:00:00 hald-addon-storage: polling /dev
root      5581  5474  0 14:19 ?        00:00:00 hald-addon-storage: polling /dev
root      5583  5474  0 14:19 ?        00:00:00 hald-addon-storage: polling /dev
root      5586  5474  0 14:19 ?        00:00:00 hald-addon-storage: polling /dev
root      5625     1  0 14:19 ?        00:00:00 /usr/sbin/hcid -x -s
root      5632     2  0 14:19 ?        00:00:00 [btaddconn]
root      5633     2  0 14:19 ?        00:00:00 [btdelconn]
root      5641  5625  0 14:19 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-se
root      5644  5625  0 14:19 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-se
root      5649     2  0 14:19 ?        00:00:00 [krfcommd]
root      5688     1  0 14:19 ?        00:00:00 /usr/sbin/gdm
root      5691  5688  0 14:19 ?        00:00:00 /usr/sbin/gdm
root      5694  5691  4 14:19 tty7     00:00:25 /usr/bin/X :0 -br -audit 0 -auth
root      5740     1  0 14:19 ?        00:00:00 /usr/sbin/anacron -s
daemon    5754     1  0 14:19 ?        00:00:00 /usr/sbin/atd
dhcp      5768  5451  0 14:19 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/d
root      5769     1  0 14:19 ?        00:00:00 /usr/sbin/cron
root      5799  5694  0 14:19 tty7     00:00:00 /usr/bin/X :0 -br -audit 0 -auth
root      5836     1  0 14:19 ?        00:00:00 /usr/sbin/apache2 -k start
root      5910     1  0 14:19 tty1     00:00:00 /sbin/getty 38400 tty1
www-data  5934  5836  0 14:19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5935  5836  0 14:19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5936  5836  0 14:19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5937  5836  0 14:19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5938  5836  0 14:19 ?        00:00:00 /usr/sbin/apache2 -k start
user     5994     1  0 14:19 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 12
user     5996     1  0 14:19 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d
user     5997  5691  0 14:19 ?        00:00:00 /usr/bin/gnome-session
user     6054  5997  0 14:19 ?        00:00:00 /usr/bin/seahorse-agent --execut
user     6058     1  0 14:19 ?        00:00:00 dbus-daemon --fork --print-addre
user     6059  5997  0 14:19 ?        00:00:00 gnome-settings-daemon
user     6063  6059  0 14:19 ?        00:00:00 /usr/bin/pulseaudio --log-target
user     6066  6063  0 14:19 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
user     6079     1  0 14:19 ?        00:00:00 gnome-screensaver
user     6084  5997  0 14:19 ?        00:00:01 /usr/bin/metacity --sm-client-id
user     6085  5997  0 14:19 ?        00:00:02 gnome-panel --sm-client-id defau
user     6087  5997  0 14:19 ?        00:00:00 nautilus --no-default-window --s
user     6091     1  0 14:19 ?        00:00:00 /usr/lib/bonobo-activation/bonob
user     6097     1  0 14:19 ?        00:00:00 /usr/lib/gvfs/gvfsd
user     6099  5997  0 14:19 ?        00:00:00 bluetooth-applet --singleton
user     6104  5997  0 14:19 ?        00:00:00 update-notifier
user     6110  5997  0 14:19 ?        00:00:00 tracker-applet
user     6111  5997  0 14:19 ?        00:00:00 /usr/lib/evolution/2.22/evolutio
user     6116  5997  0 14:19 ?        00:00:00 trackerd
user     6123     1  0 14:19 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
user     6128  5997  0 14:19 ?        00:00:00 python /usr/share/system-config-
user     6129     1  0 14:19 ?        00:00:00 /usr/lib/gnome-volume-manager/gn
user     6130  5997  0 14:19 ?        00:00:00 nm-applet --sm-disable
user     6132     1  0 14:19 ?        00:00:00 gnome-power-manager
user     6146     1  0 14:19 ?        00:00:00 /usr/lib/evolution/evolution-dat
user     6148     1  0 14:19 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
user     6151     1  0 14:19 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
user     6161     1  0 14:19 ?        00:00:00 /usr/lib/evolution/2.22/evolutio
user     6168     1  0 14:19 ?        00:00:00 mono /usr/lib/tomboy/Tomboy.exe
user     6172     1  0 14:19 ?        00:00:00 /usr/lib/gnome-applets/trashappl
user     6174     1  0 14:19 ?        00:00:00 /usr/lib/gnome-applets/mixer_app
www-data  6255  5836  0 14:20 ?        00:00:00 /usr/sbin/apache2 -k start
user     6404     1  5 14:22 ?        00:00:23 gnome-system-monitor
user     6410     1  0 14:22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
root      6445     2  0 14:23 ?        00:00:00 [pdflush]
user     6448     1  0 14:24 ?        00:00:02 gedit
root      6449  5740  0 14:24 ?        00:00:00 /bin/sh -c nice run-parts --repo
root      6450  6449  0 14:24 ?        00:00:00 run-parts --report /etc/cron.dai
root      6521     1  0 14:28 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 15
root      7164  6450  0 14:28 ?        00:00:00 /bin/sh /etc/cron.daily/mlocate
root      7165  7164  0 14:28 ?        00:00:00 /usr/bin/updatedb.mlocate
user     7168     1  3 14:29 ?        00:00:00 gnome-terminal
user     7171  7168  0 14:29 ?        00:00:00 gnome-pty-helper
user     7172  7168  1 14:29 pts/0    00:00:00 bash
user     7189  7172  0 14:29 pts/0    00:00:00 ps -ef
```

I tried ***sudo* netstat -utp** last time I got nothing, this time I got:
```
user@computer:~$ sudo netstat -utp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 computer:46920           lithium.canonical.c:www TIME_WAIT   -               
tcp        0      0 computer:49224           ubuntu.datahop.net:www  TIME_WAIT   -
```


jimv, I know that something is trying to access the internet because the light on my router keeps flashing every few seconds and **System Monitor** shows network activity.

---

