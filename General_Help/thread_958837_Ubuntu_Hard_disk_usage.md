---
title: "Ubuntu Hard disk usage"
date: 2008-10-25
forum: General Help
---

### Post by salman83 on 2008-10-25
Hi all,

I just installed ubuntu 8.04 and I am having problems with hard disk usage. I can not find any process which is taking up the whole cpu. Here is the list of all programs running.

D TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00  \_ [migration/0]
    4 ?        S<     0:00  \_ [ksoftirqd/0]
    5 ?        S<     0:00  \_ [watchdog/0]
    6 ?        S<     0:00  \_ [migration/1]
    7 ?        S<     0:00  \_ [ksoftirqd/1]
    8 ?        S<     0:00  \_ [watchdog/1]
    9 ?        S<     0:00  \_ [events/0]
   10 ?        S<     0:00  \_ [events/1]
   11 ?        S<     0:00  \_ [khelper]
   47 ?        S<     0:00  \_ [kblockd/0]
   48 ?        S<     0:00  \_ [kblockd/1]
   51 ?        S<     0:00  \_ [kacpid]
   52 ?        S<     0:00  \_ [kacpi_notify]
  140 ?        S<     0:00  \_ [kseriod]
  182 ?        S      0:00  \_ [pdflush]
  183 ?        S      0:00  \_ [pdflush]
  184 ?        S<     0:00  \_ [kswapd0]
  225 ?        S<     0:00  \_ [aio/0]
  226 ?        S<     0:00  \_ [aio/1]
 1545 ?        S<     0:00  \_ [ksuspend_usbd]
 1546 ?        S<     0:00  \_ [khubd]
 1610 ?        S<     0:00  \_ [khpsbpkt]
 1618 ?        S<     0:00  \_ [ata/0]
 1625 ?        S<     0:00  \_ [ata/1]
 1631 ?        S<     0:00  \_ [ata_aux]
 2338 ?        S<     0:00  \_ [knodemgrd_0]
 2371 ?        S<     0:00  \_ [scsi_eh_0]
 2372 ?        S<     0:00  \_ [scsi_eh_1]
 2373 ?        S<     0:00  \_ [scsi_eh_2]
 2374 ?        S<     0:00  \_ [scsi_eh_3]
 2438 ?        S<     0:00  \_ [scsi_eh_4]
 2441 ?        S<     0:00  \_ [scsi_eh_5]
 2644 ?        D<     0:00  \_ [kjournald]
 3296 ?        S<     0:00  \_ [kpsmoused]
 3315 ?        S<     0:00  \_ [kmmcd]
 5141 ?        S<     0:00  \_ [kondemand/0]
 5142 ?        S<     0:00  \_ [kondemand/1]
 5638 ?        S<     0:00  \_ [btaddconn]
 5639 ?        S<     0:00  \_ [btdelconn]
 5660 ?        S<     0:00  \_ [krfcommd]
    1 ?        Ss     0:01 /sbin/init
 2861 ?        S<s    0:00 /sbin/udevd --daemon
 4913 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4914 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4916 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4919 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4920 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5104 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 5223 ?        Ss     0:00 /sbin/syslogd -u syslog
 5277 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5280 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5302 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 5319 ?        Ss     0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
 5333 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
 5346 ?        Ss     0:00 /usr/bin/system-tools-backends
 5366 ?        Ss     0:00 avahi-daemon: running [LAPTOP-SALMAN.local]
 5367 ?        Ss     0:00  \_ avahi-daemon: chroot helper
 5410 ?        Ss     0:00 /usr/sbin/cupsd
 5484 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 5506 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 5632 ?        Ss     0:00 /usr/sbin/hcid -x -s
 5650 ?        S      0:00  \_ /usr/lib/bluetooth/bluetoothd-service-input
 5651 ?        S      0:00  \_ /usr/lib/bluetooth/bluetoothd-service-audio
 5697 ?        Ss     0:00 /usr/sbin/gdm
 5700 ?        S      0:00  \_ /usr/sbin/gdm
 5703 tty7     SLs+   0:25      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 5883 ?        Ssl    0:00      \_ x-session-manager
 5939 ?        Ss     0:00          \_ /usr/bin/seahorse-agent --execute x-session-manager
 5944 ?        Sl     0:00          \_ gnome-settings-daemon
 5948 ?        Sl     0:00          |   \_ /usr/bin/pulseaudio --log-target=syslog
 5955 ?        S      0:00          |       \_ /usr/lib/pulseaudio/pulse/gconf-helper
 5965 ?        S      0:00          \_ /bin/sh /usr/bin/compiz --sm-client-id default0
 6038 ?        SL     0:09          |   \_ /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 core ccp
 6105 ?        Ss     0:00          |       \_ /bin/sh -c /usr/bin/compiz-decorator
 6106 ?        S      0:00          |           \_ /bin/sh /usr/bin/compiz-decorator
 6108 ?        S      0:00          |               \_ /usr/bin/gtk-window-decorator
 5971 ?        S      0:01          \_ gnome-panel --sm-client-id default1
 5972 ?        S      0:00          \_ nautilus --no-default-window --sm-client-id default2
 6039 ?        S      0:00          \_ bluetooth-applet --singleton
 6042 ?        S      0:00          \_ update-notifier
 6048 ?        Sl     0:00          \_ /usr/lib/evolution/2.22/evolution-alarm-notify
 6060 ?        S      0:00          \_ python /usr/share/system-config-printer/applet.py
 6061 ?        S      0:00          \_ nm-applet --sm-disable
 5729 ?        Ss     0:00 /usr/sbin/anacron -s
 6284 ?        S      0:00  \_ /bin/sh -c nice run-parts --report /etc/cron.daily
 6285 ?        SN     0:00      \_ run-parts --report /etc/cron.daily
 6296 ?        SN     0:00          \_ /bin/sh /etc/cron.daily/apt
 6318 ?        SN     0:00              \_ sleep 1303
 5743 ?        Ss     0:00 /usr/sbin/atd
 5759 ?        Ss     0:00 /usr/sbin/cron
 5775 ?        Ss     0:00 /usr/sbin/collectdmon -P /var/run/collectdmon.pid -- -C /etc/collectd/collectd.conf
 5776 ?        Sl     0:05  \_ collectd -C /etc/collectd/collectd.conf -f
 5858 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5880 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 4
 5882 ?        S      0:00 /usr/bin/gnome-keyring-daemon -d --login
 5943 ?        Ss     0:00 dbus-daemon --fork --print-address 24 --print-pid 26 --session
 5964 ?        Ss     0:00 gnome-screensaver
 5981 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
 6000 ?        S      0:00 /usr/lib/gvfs/gvfsd
 6028 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/salman/.gvfs
 6062 ?        Ss     0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
 6064 ?        Ss     0:00 gnome-power-manager
 6072 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
 6077 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=19
 6085 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
 6117 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
 6120 ?        S      0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd
 6132 ?        Sl     0:02 gnome-terminal
 6135 ?        S      0:00  \_ gnome-pty-helper
 6136 pts/0    Ss     0:00  \_ bash
 6447 pts/0    R+     0:00      \_ ps ax --forest

I am unable to use anyother program. Please help me out!

Regards.

---

### Post by ww711 on 2008-10-25
type ```
top
``` at your commandline prompt, this will list real-time information of what's happening with your machine.

---

