---
title: "Shutdown issues"
date: 2008-10-06
forum: General Help
---

### Post by benc123 on 2008-10-06
Hello,

Im having difficulty shutting down my desktop, 8.04. It does not shut down properly if i leave it running for more than a few days. it just freezes half way through shut down.

If i dont leave the desktop on longer than a few hours then it shutdowns perfectly. 

I know this is probable not enough info to allow you to help me, so if you need more then please ask what and where i can find it as im still relatively new to Ubuntu.

Thanks benc123

---

### Post by Het Irv on 2008-10-06
Do you see any text when it shuts down?  If so, what is it?

---

### Post by benc123 on 2008-10-06
No, it is just the graphical progress bar.

---

### Post by Mr. Man on 2008-10-06
ok, so sry that i cant really help because i have no idea what the problem is, the only thing that might be causing it is that if its a laptop you close the lid before it shuts down. this happened to me on vista when i closed the lid before the computer could shut down and it went to sleep and forgot about the shutdown. im probably wrong though so sry.

---

### Post by benc123 on 2008-10-06
Any advice is appreciated. so thanks anyway. 

Is there a way to see a log of what is happening on shutdown? as this might help me to figure out what is causing the problem.

---

### Post by drubin on 2008-10-06
Try this.

```
sudo shutdown -vh now >> /var/log/shutdown.log 2>&1 
```

Use that command instead of the graphical shutdown icon. Try that when you are shutting down the pc. If there was an issue then upload that log file.

---

### Post by benc123 on 2008-10-06
Thanks, i will post what i find.

---

### Post by drubin on 2008-10-06
> **benc123 said:**
> Thanks, i will post what i find.

wait can change it to this.

```
#!/bin/bash
ps -ef >> /var/log/shutdown.log 2>&1
echo "------ MARK----- " >> /var/log/shutdown.log 2>&1
shutdown -vh now >> /var/log/shutdown.log 2>&1
```

Save that script to your desktop. myshutdown.sh
give it execute permissions (Right click permissions)

Then when you want to shutdown use this.
```
sudo ~/Desktop/myshudown.sh
```

I have added the first line so we can see what applications are currently running that could affect the shut down process.

---

### Post by benc123 on 2008-10-26
I did as you said in the last post (again the shutdown failed) but this is the log that i got from it.

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Oct22 ?        00:00:01 /sbin/init
root         2     0  0 Oct22 ?        00:00:00 [kthreadd]
root         3     2  0 Oct22 ?        00:00:00 [migration/0]
root         4     2  0 Oct22 ?        00:00:32 [ksoftirqd/0]
root         5     2  0 Oct22 ?        00:00:00 [watchdog/0]
root         6     2  0 Oct22 ?        00:00:00 [migration/1]
root         7     2  0 Oct22 ?        00:00:12 [ksoftirqd/1]
root         8     2  0 Oct22 ?        00:00:00 [watchdog/1]
root         9     2  0 Oct22 ?        00:00:00 [migration/2]
root        10     2  0 Oct22 ?        00:00:11 [ksoftirqd/2]
root        11     2  0 Oct22 ?        00:00:00 [watchdog/2]
root        12     2  0 Oct22 ?        00:00:00 [migration/3]
root        13     2  0 Oct22 ?        00:00:12 [ksoftirqd/3]
root        14     2  0 Oct22 ?        00:00:00 [watchdog/3]
root        15     2  0 Oct22 ?        00:00:02 [events/0]
root        16     2  0 Oct22 ?        00:00:25 [events/1]
root        17     2  0 Oct22 ?        00:00:01 [events/2]
root        18     2  0 Oct22 ?        00:00:01 [events/3]
root        19     2  0 Oct22 ?        00:00:00 [khelper]
root        54     2  0 Oct22 ?        00:00:08 [kblockd/0]
root        55     2  0 Oct22 ?        00:00:07 [kblockd/1]
root        56     2  0 Oct22 ?        00:00:09 [kblockd/2]
root        57     2  0 Oct22 ?        00:00:06 [kblockd/3]
root        60     2  0 Oct22 ?        00:00:00 [kacpid]
root        61     2  0 Oct22 ?        00:00:00 [kacpi_notify]
root       154     2  0 Oct22 ?        00:00:00 [kseriod]
root       213     2  0 Oct22 ?        00:00:23 [kswapd0]
root       256     2  0 Oct22 ?        00:00:00 [aio/0]
root       257     2  0 Oct22 ?        00:00:00 [aio/1]
root       258     2  0 Oct22 ?        00:00:00 [aio/2]
root       259     2  0 Oct22 ?        00:00:00 [aio/3]
root      1478     2  0 Oct22 ?        00:00:00 [ksuspend_usbd]
root      1479     2  0 Oct22 ?        00:00:00 [khubd]
root      1625     2  0 Oct22 ?        00:00:00 [khpsbpkt]
root      1630     2  0 Oct22 ?        00:00:05 [ata/0]
root      1631     2  0 Oct22 ?        00:00:05 [ata/1]
root      1632     2  0 Oct22 ?        00:00:08 [ata/2]
root      1633     2  0 Oct22 ?        00:00:04 [ata/3]
root      1634     2  0 Oct22 ?        00:00:00 [ata_aux]
root      2358     2  0 Oct22 ?        00:00:00 [knodemgrd_0]
root      2451     2  0 Oct22 ?        00:00:00 [scsi_eh_0]
root      2452     2  0 Oct22 ?        00:00:00 [scsi_eh_1]
www-data  3849  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3850  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3851  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3852  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3853  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
root      3860     2  0 07:59 ?        00:00:00 [pdflush]
root      4259     2  0 Oct22 ?        00:00:00 [scsi_eh_2]
root      4260     2  0 Oct22 ?        00:00:00 [scsi_eh_3]
root      4291     2  0 Oct22 ?        00:00:39 [scsi_eh_4]
root      4292     2  0 Oct22 ?        00:00:00 [scsi_eh_5]
root      4321     2  0 Oct22 ?        00:00:00 [scsi_eh_6]
root      4322     2  0 Oct22 ?        00:00:00 [scsi_eh_7]
root      4556     2  2 Oct22 ?        02:39:19 [kjournald]
root      4756     1  0 Oct22 ?        00:00:00 /sbin/udevd --daemon
root      5289     2  0 Oct22 ?        00:00:00 [ntos_wq]
root      5290     2  0 Oct22 ?        00:00:00 [ndis_wq]
root      5291     2  0 Oct22 ?        00:00:00 [wrapndis_wq]
root      6555     2  0 Oct22 ?        00:00:15 [kjournald]
root      6563     2  0 Oct22 ?        00:00:00 [xfslogd/0]
root      6564     2  0 Oct22 ?        00:00:00 [xfslogd/1]
root      6565     2  0 Oct22 ?        00:00:00 [xfslogd/2]
root      6566     2  0 Oct22 ?        00:00:00 [xfslogd/3]
root      6567     2  0 Oct22 ?        00:00:00 [xfsdatad/0]
root      6568     2  0 Oct22 ?        00:00:00 [xfsdatad/1]
root      6569     2  0 Oct22 ?        00:00:00 [xfsdatad/2]
root      6570     2  0 Oct22 ?        00:00:00 [xfsdatad/3]
root      6571     2  0 Oct22 ?        00:00:00 [xfs_mru_cache]
root      6572     2  0 Oct22 ?        00:00:01 [xfsbufd]
root      6580     2  0 Oct22 ?        00:00:00 [xfssyncd]
root      6876     1  0 Oct22 tty4     00:00:00 /sbin/getty 38400 tty4
root      6877     1  0 Oct22 tty5     00:00:00 /sbin/getty 38400 tty5
root      6879     1  0 Oct22 tty2     00:00:00 /sbin/getty 38400 tty2
root      6881     1  0 Oct22 tty3     00:00:00 /sbin/getty 38400 tty3
root      6883     1  0 Oct22 tty6     00:00:00 /sbin/getty 38400 tty6
root      7085     1  0 Oct22 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      7133     2  0 Oct22 ?        00:00:20 [kondemand/0]
root      7134     2  0 Oct22 ?        00:00:00 [kondemand/1]
root      7135     2  0 Oct22 ?        00:00:00 [kondemand/2]
root      7136     2  0 Oct22 ?        00:00:00 [kondemand/3]
syslog    7215     1  0 Oct22 ?        00:00:00 /sbin/syslogd -u syslog
root      7272     1  0 Oct22 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      7274     1  0 Oct22 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
106       7297     1  0 Oct22 ?        00:00:03 /usr/bin/dbus-daemon --system
root      7313     1  0 Oct22 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      7327     1  0 Oct22 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      7340     1  0 Oct22 ?        00:00:00 /usr/bin/system-tools-backends
avahi     7376     1  0 Oct22 ?        00:00:02 avahi-daemon: running [benc-desktop.local]
avahi     7377  7376  0 Oct22 ?        00:00:00 avahi-daemon: chroot helper
root      7428     1  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     7470  7428  0 Oct22 ?        00:27:38 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      7471  7428  0 Oct22 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      7557     1  0 Oct22 ?        00:00:00 /usr/sbin/cupsd
root      7614     1  0 Oct22 ?        00:00:13 /usr/sbin/nmbd -D
root      7616     1  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
root      7634  7616  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
dhcp      7656     1  0 Oct22 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root      7734     1  0 Oct22 ?        00:00:00 /usr/bin/xfs -daemon
root      7782     1  0 Oct22 ?        00:00:06 /usr/sbin/dhcdbd --system
109       7801     1  0 Oct22 ?        00:00:03 /usr/sbin/hald
root      7806     1  0 Oct22 ?        00:00:00 /usr/sbin/console-kit-daemon
root      7807  7801  0 Oct22 ?        00:00:00 hald-runner
root      7890  7807  0 Oct22 ?        00:00:10 hald-addon-input: Listening on /dev/input/event2 /dev/input/event1 /dev/input/event6 /dev/input/event4 /dev/input/event5
root      7901  7807  0 Oct22 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
109       7902  7807  0 Oct22 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      7956  7807  0 Oct22 ?        00:00:42 hald-addon-storage: polling /dev/scd0 (every 2 sec)
mythtv    7986     1  0 Oct22 ?        00:42:45 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
root      8013     1  0 Oct22 ?        00:00:00 /usr/sbin/hcid -x -s
root      8024     2  0 Oct22 ?        00:00:00 [btaddconn]
root      8025     2  0 Oct22 ?        00:00:00 [btdelconn]
root      8047     2  0 Oct22 ?        00:00:00 [krfcommd]
root      8050  8013  0 Oct22 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      8081  8013  0 Oct22 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-input
root      8090     1  0 Oct22 ?        00:00:00 /usr/sbin/gdm
root      8156     1  0 Oct22 ?        00:00:02 /usr/sbin/lircd --driver=devinput --device=/dev/lirc1
daemon    8189     1  0 Oct22 ?        00:00:00 /usr/sbin/atd
root      8203     1  0 Oct22 ?        00:00:00 /usr/sbin/cron
root      8235     1  0 Oct22 ?        00:00:04 /usr/sbin/apache2 -k start
root      8309     1  0 Oct22 tty1     00:00:00 /sbin/getty 38400 tty1
benc      8330     1  0 Oct22 ?        00:00:16 /usr/lib/libgconf2-4/gconfd-2 4
105       8337     1  0 Oct22 ?        00:00:00 avahi-autoipd: [wlan0] bound 169.254.3.126
root      8338  8337  0 Oct22 ?        00:00:00 avahi-autoipd: [wlan0] callout dispatcher
benc      8453     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc      8490     1  0 Oct22 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
benc      8515     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
dhcp      8543     1  0 Oct22 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
benc      8610     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/benc/.gvfs
ntp       8641     1  0 Oct22 ?        00:00:05 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 113:125 -g
benc      8658     1  0 Oct22 ?        00:00:00 trackerd
benc      8673     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc      8699     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/2
benc      8714     1  0 Oct22 ?        00:00:00 /usr/lib/evolution/evolution-data-server-2.22 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=30
benc      8888     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc      9157     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc      9204     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc      9222     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc      9279     1  0 Oct22 ?        00:00:00 trackerd
benc      9331     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc      9422     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc     10003     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     10049     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     10067     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     10124     1  0 Oct22 ?        00:00:00 trackerd
benc     10162     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     10378     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     10428     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     10444     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     10497     1  0 Oct22 ?        00:00:00 trackerd
benc     10535     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     10628     1 12 15:33 ?        00:00:06 /usr/lib/firefox-3.0.3/firefox
benc     10676 10628  0 15:33 ?        00:00:00 [npviewer.bin] <defunct>
benc     10695     1  0 15:33 ?        00:00:00 gnome-terminal
benc     10697 10695  0 15:33 ?        00:00:00 gnome-pty-helper
benc     10698 10695  0 15:33 pts/0    00:00:00 bash
root     10715 10698  0 15:34 pts/0    00:00:00 /bin/bash /home/benc/Desktop/myshutdown.sh
root     10716 10715  0 15:34 pts/0    00:00:00 ps -ef
benc     10763     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     10804     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     10829     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     10887     1  0 Oct22 ?        00:00:00 trackerd
benc     10943     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     11191     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     11236     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     11261     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     11316     1  0 Oct22 ?        00:00:00 trackerd
benc     11353     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     11778     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     11826     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     11845     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     11902     1  0 Oct22 ?        00:00:00 trackerd
benc     11941     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
root     14157     2  0 Oct25 ?        00:00:05 [pdflush]
benc     16491     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     16534     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     16556     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     16615     1  0 Oct22 ?        00:00:00 trackerd
benc     16668     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     16875     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc     17034     1  0 Oct25 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc     17270     1  0 Oct22 ?        00:00:00 /usr/bin/totem-audio-preview
root     17358     1  0 Oct22 ?        00:00:00 /usr/bin/perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
benc     17580     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     17626     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     17648     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     17705     1  0 Oct22 ?        00:00:00 trackerd
benc     17746     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     18008     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     18061     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     18074     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     18130     1  0 Oct22 ?        00:00:00 trackerd
benc     18172     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     18540     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     18582     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     18606     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     18661     1  0 Oct22 ?        00:00:00 trackerd
benc     18702     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     18962     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     19005     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     19028     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     19085     1  0 Oct22 ?        00:00:00 trackerd
benc     19119     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     19495     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     19543     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     19561     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     19617     1  0 Oct22 ?        00:00:00 trackerd
benc     19658     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     20087     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     20135     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     20155     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     20209     1  0 Oct22 ?        00:00:00 trackerd
benc     20249     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     20522     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     20569     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     20589     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     20646     1  0 Oct22 ?        00:00:00 trackerd
benc     20686     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     20777     1  0 Oct22 ?        00:00:00 /usr/bin/totem-audio-preview file:///home/benc/Desktop/startup.wav
benc     21028     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     21078     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     21093     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     21150     1  0 Oct22 ?        00:00:00 trackerd
benc     21184     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     21395     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     21437     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     21459     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     21517     1  0 Oct22 ?        00:00:00 trackerd
benc     21560     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     21941     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     21985     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     22014     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     22064     1  0 Oct22 ?        00:00:00 trackerd
benc     22106     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     22398     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     22442     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     22463     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     22522     1  0 Oct22 ?        00:00:00 trackerd
benc     22556     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     22975     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     23014     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     23038     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     23100     1  0 Oct22 ?        00:00:00 trackerd
benc     23137     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     24308     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     24359     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     24376     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     24431     1  0 Oct22 ?        00:00:00 trackerd
benc     24481     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     25078     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     25119     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     25143     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     25199     1  0 Oct22 ?        00:00:00 trackerd
benc     25246     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
root     25449  8090  0 Oct22 ?        00:00:00 /usr/sbin/gdm
root     25480 25449  2 Oct22 tty7     02:06:52 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
benc     25499     1  0 Oct22 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d --login
benc     25500 25449  0 Oct22 ?        00:00:02 /usr/bin/gnome-session
benc     25608 25500  0 Oct22 ?        00:00:00 /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
benc     25615     1  0 Oct22 ?        00:00:03 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     25617 25500  0 Oct22 ?        00:00:51 gnome-settings-daemon
benc     25621 25617  1 Oct22 ?        00:59:53 /usr/bin/pulseaudio --log-target=syslog
benc     25624 25621  0 Oct22 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
benc     25633 25500  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/compiz --sm-client-id default0
benc     25634 25500  0 Oct22 ?        00:00:29 gnome-panel --sm-client-id default1
benc     25642 25500  0 Oct22 ?        00:02:08 nautilus --no-default-window --sm-client-id default2
benc     25646     1  0 Oct22 ?        00:06:29 gnome-screensaver
benc     25664     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     25685     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     25695     1  0 Oct22 ?        00:00:04 mono /usr/lib/tomboy/Tomboy.exe --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=19
benc     25699     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=22
benc     25701     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=31
benc     25707     1  1 Oct22 ?        01:30:43 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=25
benc     25723 25633  3 Oct22 ?        03:36:02 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 core ccp
benc     25724 25500  0 Oct22 ?        00:00:00 bluetooth-applet --singleton
benc     25727 25500  0 Oct22 ?        00:00:03 update-notifier
benc     25730 25500  0 Oct22 ?        00:00:00 tracker-applet
benc     25732 25500  0 Oct22 ?        00:00:00 /usr/lib/evolution/2.22/evolution-alarm-notify
benc     25736 25500  0 Oct22 ?        00:00:00 trackerd
benc     25738 25500  0 Oct22 ?        00:52:42 mythbackend
benc     25739 25500  0 Oct22 ?        00:01:48 avant-window-navigator
benc     25744 25500  0 Oct22 ?        00:00:01 python /usr/share/system-config-printer/applet.py
benc     25745 25500  0 Oct22 ?        00:01:34 nm-applet --sm-disable
benc     25748     1  0 Oct22 ?        00:00:03 gnome-power-manager
benc     25755     1  0 Oct22 ?        00:00:01 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
root     25758     2  0 Oct22 ?        00:00:47 [kdvb-fe-0]
benc     25762     1  0 Oct22 ?        00:00:00 /usr/lib/evolution/2.22/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=27
root     25771     2  0 Oct22 ?        00:00:45 [kdvb-fe-1]
benc     25772 25723  0 Oct22 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
benc     25773 25772  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/compiz-decorator
benc     25775 25773  0 Oct22 ?        00:00:12 /usr/bin/gtk-window-decorator
benc     25777     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     25933     1  0 Oct22 ?        00:00:05 /usr/lib/notification-daemon/notification-daemon
benc     27347     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-network --spawner :1.4 /org/gtk/gvfs/exec_spaw/2
benc     27349     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-smb-browse --spawner :1.4 /org/gtk/gvfs/exec_spaw/3
root     27355  7616  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
benc     27357     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.4 /org/gtk/gvfs/exec_spaw/6
root     27363  7616  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
benc     27382     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.4 /org/gtk/gvfs/exec_spaw/7
benc     27721     1  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/gmail-notify
benc     27722 27721  0 Oct22 ?        00:00:58 python ./notifier.py
------ MARK----- 

It makes on sense to me.
Can you figure out whats wrong?

Thanx benc123

---

### Post by drubin on 2008-10-26
> **benc123 said:**
> I did as you said in the last post (again the shutdown failed) but this is the log that i got from it.
> 
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Oct22 ?        00:00:01 /sbin/init
root         2     0  0 Oct22 ?        00:00:00 [kthreadd]
root         3     2  0 Oct22 ?        00:00:00 [migration/0]
root         4     2  0 Oct22 ?        00:00:32 [ksoftirqd/0]
root         5     2  0 Oct22 ?        00:00:00 [watchdog/0]
root         6     2  0 Oct22 ?        00:00:00 [migration/1]
root         7     2  0 Oct22 ?        00:00:12 [ksoftirqd/1]
root         8     2  0 Oct22 ?        00:00:00 [watchdog/1]
root         9     2  0 Oct22 ?        00:00:00 [migration/2]
root        10     2  0 Oct22 ?        00:00:11 [ksoftirqd/2]
root        11     2  0 Oct22 ?        00:00:00 [watchdog/2]
root        12     2  0 Oct22 ?        00:00:00 [migration/3]
root        13     2  0 Oct22 ?        00:00:12 [ksoftirqd/3]
root        14     2  0 Oct22 ?        00:00:00 [watchdog/3]
root        15     2  0 Oct22 ?        00:00:02 [events/0]
root        16     2  0 Oct22 ?        00:00:25 [events/1]
root        17     2  0 Oct22 ?        00:00:01 [events/2]
root        18     2  0 Oct22 ?        00:00:01 [events/3]
root        19     2  0 Oct22 ?        00:00:00 [khelper]
root        54     2  0 Oct22 ?        00:00:08 [kblockd/0]
root        55     2  0 Oct22 ?        00:00:07 [kblockd/1]
root        56     2  0 Oct22 ?        00:00:09 [kblockd/2]
root        57     2  0 Oct22 ?        00:00:06 [kblockd/3]
root        60     2  0 Oct22 ?        00:00:00 [kacpid]
root        61     2  0 Oct22 ?        00:00:00 [kacpi_notify]
root       154     2  0 Oct22 ?        00:00:00 [kseriod]
root       213     2  0 Oct22 ?        00:00:23 [kswapd0]
root       256     2  0 Oct22 ?        00:00:00 [aio/0]
root       257     2  0 Oct22 ?        00:00:00 [aio/1]
root       258     2  0 Oct22 ?        00:00:00 [aio/2]
root       259     2  0 Oct22 ?        00:00:00 [aio/3]
root      1478     2  0 Oct22 ?        00:00:00 [ksuspend_usbd]
root      1479     2  0 Oct22 ?        00:00:00 [khubd]
root      1625     2  0 Oct22 ?        00:00:00 [khpsbpkt]
root      1630     2  0 Oct22 ?        00:00:05 [ata/0]
root      1631     2  0 Oct22 ?        00:00:05 [ata/1]
root      1632     2  0 Oct22 ?        00:00:08 [ata/2]
root      1633     2  0 Oct22 ?        00:00:04 [ata/3]
root      1634     2  0 Oct22 ?        00:00:00 [ata_aux]
root      2358     2  0 Oct22 ?        00:00:00 [knodemgrd_0]
root      2451     2  0 Oct22 ?        00:00:00 [scsi_eh_0]
root      2452     2  0 Oct22 ?        00:00:00 [scsi_eh_1]
www-data  3849  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3850  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3851  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3852  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3853  8235  0 07:58 ?        00:00:00 /usr/sbin/apache2 -k start
root      3860     2  0 07:59 ?        00:00:00 [pdflush]
root      4259     2  0 Oct22 ?        00:00:00 [scsi_eh_2]
root      4260     2  0 Oct22 ?        00:00:00 [scsi_eh_3]
root      4291     2  0 Oct22 ?        00:00:39 [scsi_eh_4]
root      4292     2  0 Oct22 ?        00:00:00 [scsi_eh_5]
root      4321     2  0 Oct22 ?        00:00:00 [scsi_eh_6]
root      4322     2  0 Oct22 ?        00:00:00 [scsi_eh_7]
root      4556     2  2 Oct22 ?        02:39:19 [kjournald]
root      4756     1  0 Oct22 ?        00:00:00 /sbin/udevd --daemon
root      5289     2  0 Oct22 ?        00:00:00 [ntos_wq]
root      5290     2  0 Oct22 ?        00:00:00 [ndis_wq]
root      5291     2  0 Oct22 ?        00:00:00 [wrapndis_wq]
root      6555     2  0 Oct22 ?        00:00:15 [kjournald]
root      6563     2  0 Oct22 ?        00:00:00 [xfslogd/0]
root      6564     2  0 Oct22 ?        00:00:00 [xfslogd/1]
root      6565     2  0 Oct22 ?        00:00:00 [xfslogd/2]
root      6566     2  0 Oct22 ?        00:00:00 [xfslogd/3]
root      6567     2  0 Oct22 ?        00:00:00 [xfsdatad/0]
root      6568     2  0 Oct22 ?        00:00:00 [xfsdatad/1]
root      6569     2  0 Oct22 ?        00:00:00 [xfsdatad/2]
root      6570     2  0 Oct22 ?        00:00:00 [xfsdatad/3]
root      6571     2  0 Oct22 ?        00:00:00 [xfs_mru_cache]
root      6572     2  0 Oct22 ?        00:00:01 [xfsbufd]
root      6580     2  0 Oct22 ?        00:00:00 [xfssyncd]
root      6876     1  0 Oct22 tty4     00:00:00 /sbin/getty 38400 tty4
root      6877     1  0 Oct22 tty5     00:00:00 /sbin/getty 38400 tty5
root      6879     1  0 Oct22 tty2     00:00:00 /sbin/getty 38400 tty2
root      6881     1  0 Oct22 tty3     00:00:00 /sbin/getty 38400 tty3
root      6883     1  0 Oct22 tty6     00:00:00 /sbin/getty 38400 tty6
root      7085     1  0 Oct22 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      7133     2  0 Oct22 ?        00:00:20 [kondemand/0]
root      7134     2  0 Oct22 ?        00:00:00 [kondemand/1]
root      7135     2  0 Oct22 ?        00:00:00 [kondemand/2]
root      7136     2  0 Oct22 ?        00:00:00 [kondemand/3]
syslog    7215     1  0 Oct22 ?        00:00:00 /sbin/syslogd -u syslog
root      7272     1  0 Oct22 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      7274     1  0 Oct22 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
106       7297     1  0 Oct22 ?        00:00:03 /usr/bin/dbus-daemon --system
root      7313     1  0 Oct22 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      7327     1  0 Oct22 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      7340     1  0 Oct22 ?        00:00:00 /usr/bin/system-tools-backends
avahi     7376     1  0 Oct22 ?        00:00:02 avahi-daemon: running [benc-desktop.local]
avahi     7377  7376  0 Oct22 ?        00:00:00 avahi-daemon: chroot helper
root      7428     1  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     7470  7428  0 Oct22 ?        00:27:38 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      7471  7428  0 Oct22 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      7557     1  0 Oct22 ?        00:00:00 /usr/sbin/cupsd
root      7614     1  0 Oct22 ?        00:00:13 /usr/sbin/nmbd -D
root      7616     1  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
root      7634  7616  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
dhcp      7656     1  0 Oct22 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root      7734     1  0 Oct22 ?        00:00:00 /usr/bin/xfs -daemon
root      7782     1  0 Oct22 ?        00:00:06 /usr/sbin/dhcdbd --system
109       7801     1  0 Oct22 ?        00:00:03 /usr/sbin/hald
root      7806     1  0 Oct22 ?        00:00:00 /usr/sbin/console-kit-daemon
root      7807  7801  0 Oct22 ?        00:00:00 hald-runner
root      7890  7807  0 Oct22 ?        00:00:10 hald-addon-input: Listening on /dev/input/event2 /dev/input/event1 /dev/input/event6 /dev/input/event4 /dev/input/event5
root      7901  7807  0 Oct22 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
109       7902  7807  0 Oct22 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      7956  7807  0 Oct22 ?        00:00:42 hald-addon-storage: polling /dev/scd0 (every 2 sec)
mythtv    7986     1  0 Oct22 ?        00:42:45 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
root      8013     1  0 Oct22 ?        00:00:00 /usr/sbin/hcid -x -s
root      8024     2  0 Oct22 ?        00:00:00 [btaddconn]
root      8025     2  0 Oct22 ?        00:00:00 [btdelconn]
root      8047     2  0 Oct22 ?        00:00:00 [krfcommd]
root      8050  8013  0 Oct22 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      8081  8013  0 Oct22 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-input
root      8090     1  0 Oct22 ?        00:00:00 /usr/sbin/gdm
root      8156     1  0 Oct22 ?        00:00:02 /usr/sbin/lircd --driver=devinput --device=/dev/lirc1
daemon    8189     1  0 Oct22 ?        00:00:00 /usr/sbin/atd
root      8203     1  0 Oct22 ?        00:00:00 /usr/sbin/cron
root      8235     1  0 Oct22 ?        00:00:04 /usr/sbin/apache2 -k start
root      8309     1  0 Oct22 tty1     00:00:00 /sbin/getty 38400 tty1
benc      8330     1  0 Oct22 ?        00:00:16 /usr/lib/libgconf2-4/gconfd-2 4
105       8337     1  0 Oct22 ?        00:00:00 avahi-autoipd: [wlan0] bound 169.254.3.126
root      8338  8337  0 Oct22 ?        00:00:00 avahi-autoipd: [wlan0] callout dispatcher
benc      8453     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc      8490     1  0 Oct22 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
benc      8515     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
dhcp      8543     1  0 Oct22 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
benc      8610     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/benc/.gvfs
ntp       8641     1  0 Oct22 ?        00:00:05 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 113:125 -g
benc      8658     1  0 Oct22 ?        00:00:00 trackerd
benc      8673     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc      8699     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/2
benc      8714     1  0 Oct22 ?        00:00:00 /usr/lib/evolution/evolution-data-server-2.22 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=30
benc      8888     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc      9157     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc      9204     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc      9222     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc      9279     1  0 Oct22 ?        00:00:00 trackerd
benc      9331     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc      9422     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc     10003     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     10049     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     10067     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     10124     1  0 Oct22 ?        00:00:00 trackerd
benc     10162     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     10378     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     10428     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     10444     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     10497     1  0 Oct22 ?        00:00:00 trackerd
benc     10535     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     10628     1 12 15:33 ?        00:00:06 /usr/lib/firefox-3.0.3/firefox
benc     10676 10628  0 15:33 ?        00:00:00 [npviewer.bin] <defunct>
benc     10695     1  0 15:33 ?        00:00:00 gnome-terminal
benc     10697 10695  0 15:33 ?        00:00:00 gnome-pty-helper
benc     10698 10695  0 15:33 pts/0    00:00:00 bash
root     10715 10698  0 15:34 pts/0    00:00:00 /bin/bash /home/benc/Desktop/myshutdown.sh
root     10716 10715  0 15:34 pts/0    00:00:00 ps -ef
benc     10763     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     10804     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     10829     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     10887     1  0 Oct22 ?        00:00:00 trackerd
benc     10943     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     11191     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     11236     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     11261     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     11316     1  0 Oct22 ?        00:00:00 trackerd
benc     11353     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     11778     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     11826     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     11845     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     11902     1  0 Oct22 ?        00:00:00 trackerd
benc     11941     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
root     14157     2  0 Oct25 ?        00:00:05 [pdflush]
benc     16491     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     16534     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     16556     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     16615     1  0 Oct22 ?        00:00:00 trackerd
benc     16668     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     16875     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc     17034     1  0 Oct25 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
benc     17270     1  0 Oct22 ?        00:00:00 /usr/bin/totem-audio-preview
root     17358     1  0 Oct22 ?        00:00:00 /usr/bin/perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
benc     17580     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     17626     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     17648     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     17705     1  0 Oct22 ?        00:00:00 trackerd
benc     17746     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     18008     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     18061     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     18074     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     18130     1  0 Oct22 ?        00:00:00 trackerd
benc     18172     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     18540     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     18582     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     18606     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     18661     1  0 Oct22 ?        00:00:00 trackerd
benc     18702     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     18962     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     19005     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     19028     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     19085     1  0 Oct22 ?        00:00:00 trackerd
benc     19119     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     19495     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     19543     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     19561     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     19617     1  0 Oct22 ?        00:00:00 trackerd
benc     19658     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     20087     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     20135     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     20155     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     20209     1  0 Oct22 ?        00:00:00 trackerd
benc     20249     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     20522     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     20569     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     20589     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     20646     1  0 Oct22 ?        00:00:00 trackerd
benc     20686     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     20777     1  0 Oct22 ?        00:00:00 /usr/bin/totem-audio-preview file:///home/benc/Desktop/startup.wav
benc     21028     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     21078     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     21093     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     21150     1  0 Oct22 ?        00:00:00 trackerd
benc     21184     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     21395     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     21437     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     21459     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     21517     1  0 Oct22 ?        00:00:00 trackerd
benc     21560     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     21941     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     21985     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     22014     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     22064     1  0 Oct22 ?        00:00:00 trackerd
benc     22106     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     22398     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     22442     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     22463     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     22522     1  0 Oct22 ?        00:00:00 trackerd
benc     22556     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     22975     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     23014     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     23038     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     23100     1  0 Oct22 ?        00:00:00 trackerd
benc     23137     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     24308     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     24359     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     24376     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     24431     1  0 Oct22 ?        00:00:00 trackerd
benc     24481     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     25078     1  0 Oct22 ?        00:00:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     25119     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     25143     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     25199     1  0 Oct22 ?        00:00:00 trackerd
benc     25246     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
root     25449  8090  0 Oct22 ?        00:00:00 /usr/sbin/gdm
root     25480 25449  2 Oct22 tty7     02:06:52 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
benc     25499     1  0 Oct22 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d --login
benc     25500 25449  0 Oct22 ?        00:00:02 /usr/bin/gnome-session
benc     25608 25500  0 Oct22 ?        00:00:00 /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
benc     25615     1  0 Oct22 ?        00:00:03 dbus-daemon --fork --print-address 20 --print-pid 22 --session
benc     25617 25500  0 Oct22 ?        00:00:51 gnome-settings-daemon
benc     25621 25617  1 Oct22 ?        00:59:53 /usr/bin/pulseaudio --log-target=syslog
benc     25624 25621  0 Oct22 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
benc     25633 25500  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/compiz --sm-client-id default0
benc     25634 25500  0 Oct22 ?        00:00:29 gnome-panel --sm-client-id default1
benc     25642 25500  0 Oct22 ?        00:02:08 nautilus --no-default-window --sm-client-id default2
benc     25646     1  0 Oct22 ?        00:06:29 gnome-screensaver
benc     25664     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd
benc     25685     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
benc     25695     1  0 Oct22 ?        00:00:04 mono /usr/lib/tomboy/Tomboy.exe --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=19
benc     25699     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=22
benc     25701     1  0 Oct22 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=31
benc     25707     1  1 Oct22 ?        01:30:43 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=25
benc     25723 25633  3 Oct22 ?        03:36:02 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 core ccp
benc     25724 25500  0 Oct22 ?        00:00:00 bluetooth-applet --singleton
benc     25727 25500  0 Oct22 ?        00:00:03 update-notifier
benc     25730 25500  0 Oct22 ?        00:00:00 tracker-applet
benc     25732 25500  0 Oct22 ?        00:00:00 /usr/lib/evolution/2.22/evolution-alarm-notify
benc     25736 25500  0 Oct22 ?        00:00:00 trackerd
benc     25738 25500  0 Oct22 ?        00:52:42 mythbackend
benc     25739 25500  0 Oct22 ?        00:01:48 avant-window-navigator
benc     25744 25500  0 Oct22 ?        00:00:01 python /usr/share/system-config-printer/applet.py
benc     25745 25500  0 Oct22 ?        00:01:34 nm-applet --sm-disable
benc     25748     1  0 Oct22 ?        00:00:03 gnome-power-manager
benc     25755     1  0 Oct22 ?        00:00:01 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
root     25758     2  0 Oct22 ?        00:00:47 [kdvb-fe-0]
benc     25762     1  0 Oct22 ?        00:00:00 /usr/lib/evolution/2.22/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=27
root     25771     2  0 Oct22 ?        00:00:45 [kdvb-fe-1]
benc     25772 25723  0 Oct22 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
benc     25773 25772  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/compiz-decorator
benc     25775 25773  0 Oct22 ?        00:00:12 /usr/bin/gtk-window-decorator
benc     25777     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
benc     25933     1  0 Oct22 ?        00:00:05 /usr/lib/notification-daemon/notification-daemon
benc     27347     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-network --spawner :1.4 /org/gtk/gvfs/exec_spaw/2
benc     27349     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-smb-browse --spawner :1.4 /org/gtk/gvfs/exec_spaw/3
root     27355  7616  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
benc     27357     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.4 /org/gtk/gvfs/exec_spaw/6
root     27363  7616  0 Oct22 ?        00:00:00 /usr/sbin/smbd -D
benc     27382     1  0 Oct22 ?        00:00:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.4 /org/gtk/gvfs/exec_spaw/7
benc     27721     1  0 Oct22 ?        00:00:00 /bin/sh /usr/bin/gmail-notify
benc     27722 27721  0 Oct22 ?        00:00:58 python ./notifier.py
------ MARK----- 

It makes on sense to me.
Can you figure out whats wrong?

Thanx benc123

Ok I am not a Linux Guru. but this log would help others to figure out what is going on.

3 Things I found very weired straight off the bat. 
[LIST=1]
[*]There is NOTHING after ----MARK ---. 
[*]There are multiple versions of the same application running.
[*]I have never heard of a /org dir being on standard Linux machines. "/org/gtk/gvfs/exec_spaw/0..."
[/LIST]

---

### Post by benc123 on 2008-10-26
Thanx for your help drubin, and everyone else. If anyone has any further ideas on this matter i would love to hear from you. 

Benc123

---

