---
title: "95% of 768mb of mem full at boot???"
date: 2008-09-10
forum: General Help
---

### Post by csmeder on 2008-09-10
First question: What does 
```
memory: 
40% in use by programs 
55% in use as cache
``` 

mean?

Second question why does my system (running ubuntu 8.04 with 512mb + 256mb ram) use so much memory up at boot?

running the command: 
```
echo; ps aux | head -1 ; ps aux | sort -rn -k 4 
```
results in:
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
n         6018  6.0  9.9 233304 76060 ?        Sl   03:07   1:27 /usr/lib/firefox-3.0.1/firefox
root      5357  3.6  5.5  50184 42812 tty7     Rs+  03:06   0:55 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
n         5729  0.0  3.0 105184 23500 ?        S    03:07   0:01 nautilus --no-default-window --sm-client-id default2
n         6127  0.9  2.8 132568 22128 ?        Sl   03:09   0:12 gnome-terminal
n         5728  0.3  2.6  75628 20044 ?        S    03:07   0:05 gnome-panel --sm-client-id default1
n         5686  0.0  2.2  46320 17048 ?        Sl   03:07   0:00 gnome-settings-daemon
n         5771  0.0  1.8  75128 14348 ?        Sl   03:07   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=29
n         5820  0.0  1.7  26000 13608 ?        S    03:07   0:00 python /usr/share/system-config-printer/applet.py
n         5612  0.0  1.7  73236 13348 ?        Ssl  03:07   0:00 x-session-manager
n         5759  0.4  1.6  64756 12940 ?        S    03:07   0:06 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=21
n         5752  0.0  1.6  64468 12632 ?        S    03:07   0:00 update-notifier
n         5811  0.1  1.5 104492 11860 ?        S    03:07   0:02 nm-applet --sm-disable
n         5871  0.0  1.4  63860 11052 ?        S    03:07   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=23
n         5824  0.0  1.3  66332 10004 ?        Ss   03:07   0:00 gnome-power-manager
n         5768  0.0  1.3  63624 10544 ?        S    03:07   0:00 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-iid=OAFIID:GNOME_NetstatusApplet_Factory --oaf-ior-fd=22
n         5726  0.3  1.2  17728  9800 ?        S    03:07   0:04 /usr/bin/metacity --sm-client-id=default0
n         5772  0.6  1.1  28260  8456 ?        SNl  03:07   0:09 trackerd
n         5755  0.0  1.0  17980  7840 ?        S    03:07   0:00 tracker-applet
n         5738  0.0  0.9  16500  7332 ?        S    03:07   0:00 bluetooth-applet --singleton
n         5671  0.0  0.8  23532  6576 ?        Ss   03:07   0:00 /usr/bin/seahorse-agent --execute x-session-manager
n         5812  0.0  0.6  21608  5020 ?        Ss   03:07   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
n         5673  0.4  0.6  13592  4620 ?        S    03:07   0:06 /usr/lib/at-spi/at-spi-registryd
Slmodemd  4906  0.0  0.5   3964  3980 ?        SL   03:06   0:00 /usr/sbin/slmodemd --alsa -c USA modem:1
n         5705  0.0  0.5  26964  4240 ?        Sl   03:07   0:00 /usr/bin/pulseaudio --log-target=syslog
n         5609  0.0  0.5   7288  4356 ?        S    03:07   0:00 /usr/lib/libgconf2-4/gconfd-2 4
107       5170  0.0  0.5   6176  4196 ?        Ss   03:06   0:01 /usr/sbin/hald
n         6130  0.0  0.4   6256  3668 pts/1    Rs   03:09   0:00 bash
n         5676  0.0  0.4  31912  3156 ?        Ssl  03:07   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=13
root      5353  0.0  0.3  14516  2980 ?        S    03:06   0:00 /usr/sbin/gdm
root      5173  0.0  0.3   7884  2384 ?        Ssl  03:06   0:00 /usr/sbin/console-kit-daemon
root      5046  0.0  0.3   6048  2364 ?        Ss   03:06   0:00 /usr/sbin/cupsd
root      4806  0.0  0.3  21208  2320 ?        Ssl  03:06   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
n         5810  0.0  0.3  22036  2640 ?        S    03:07   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
n         5721  0.1  0.3  16584  3020 ?        Ss   03:07   0:01 gnome-screensaver
root      5350  0.0  0.2  14060  1600 ?        Ss   03:06   0:00 /usr/sbin/gdm
root         1  0.0  0.2   2844  1688 ?        Ss   03:06   0:01 /sbin/init
n         5822  0.0  0.2   5372  2140 ?        S    03:07   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
n         5737  0.0  0.2   5372  2092 ?        S    03:07   0:00 /usr/lib/gvfs/gvfsd
n         5708  0.0  0.2   5776  2260 ?        S    03:07   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
n         5611  0.0  0.2  14340  2104 ?        S    03:07   0:00 /usr/bin/gnome-keyring-daemon -d --login
klog      4768  0.0  0.2   3300  2144 ?        Ss   03:06   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      5907  0.0  0.1   3880  1524 ?        S    03:07   0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
root      5409  0.0  0.1   2104   892 ?        Ss   03:06   0:00 /usr/sbin/cron
root      5287  0.0  0.1   3420  1140 ?        S    03:06   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5259  0.0  0.1   3428  1228 ?        S    03:06   0:00 /usr/lib/hal/hald-addon-cpufreq
root      5248  0.0  0.1   3416  1152 ?        S    03:06   0:00 hald-addon-input: Listening on /dev/input/event7 /dev/input/event1 /dev/input/event4 /dev/input/event5 /dev/input/event6
root      5235  0.0  0.1   3352  1164 ?        S    03:06   0:00 hald-runner
root      5169  0.0  0.1   8084  1060 ?        S    03:06   0:00 /usr/sbin/winbindd
root      5150  0.0  0.1   2020   904 ?        Ss   03:06   0:00 /usr/sbin/dhcdbd --system
root      5109  0.0  0.1   8084  1288 ?        Ss   03:06   0:00 /usr/sbin/winbindd
root      4833  0.0  0.1   4112  1104 ?        Ss   03:06   0:00 /usr/bin/system-tools-backends
root      4820  0.0  0.1   3536  1312 ?        Ss   03:06   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4605  0.0  0.1   2456  1428 ?        Ss   03:06   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      2680  0.0  0.1   2456  1000 ?        S<s  03:06   0:00 /sbin/udevd --daemon
n         7381  0.0  0.1  28716   792 pts/1    R+   03:32   0:00 sort -rn -k 4
n         7380  0.0  0.1   2644  1004 pts/1    R+   03:32   0:00 ps aux
n         6129  0.0  0.1   2912   852 ?        S    03:09   0:00 gnome-pty-helper
n         5685  0.0  0.1   2696  1088 ?        Ss   03:07   0:00 dbus-daemon --fork --print-address 24 --print-pid 26 --session
dhcp      5934  0.0  0.1   2440  1184 ?        S    03:07   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.leases -pf /var/run/dhclient.eth1.pid -q -e dhc_dbus=31 -d eth1
avahi     4960  0.0  0.1   2760  1420 ?        Ss   03:06   0:00 avahi-daemon: running [NewYork2.local]
107       5260  0.0  0.1   2204   960 ?        S    03:06   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
103       4790  0.1  0.1   2772  1272 ?        Ss   03:06   0:01 /usr/bin/dbus-daemon --system
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
syslog    4713  0.0  0.0   1936   652 ?        Ss   03:06   0:00 /sbin/syslogd -u syslog
root         7  0.0  0.0      0     0 ?        S<   03:06   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   03:06   0:00 [events/0]
root      5695  0.0  0.0   1748   356 ?        S<s  03:07   0:00 avahi-autoipd: [eth0] callout dispatcher
root      5581  0.0  0.0   1716   508 tty1     Ss+  03:07   0:00 /sbin/getty 38400 tty1
root         5  0.0  0.0      0     0 ?        S<   03:06   0:00 [watchdog/0]
root      4766  0.0  0.0   1872   540 ?        S    03:06   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
root      4642  0.2  0.0      0     0 ?        S<   03:06   0:03 [kondemand/0]
root        45  0.0  0.0      0     0 ?        S<   03:06   0:00 [kacpi_notify]
root      4431  0.0  0.0   1716   508 tty6     Ss+  03:06   0:00 /sbin/getty 38400 tty6
root      4429  0.0  0.0   1716   512 tty3     Ss+  03:06   0:00 /sbin/getty 38400 tty3
root      4428  0.0  0.0   1716   512 tty2     Ss+  03:06   0:00 /sbin/getty 38400 tty2
root      4424  0.0  0.0   1716   508 tty5     Ss+  03:06   0:00 /sbin/getty 38400 tty5
root      4423  0.0  0.0   1716   512 tty4     Ss+  03:06   0:00 /sbin/getty 38400 tty4
root        44  0.0  0.0      0     0 ?        S<   03:06   0:00 [kacpid]
root        41  0.0  0.0      0     0 ?        S<   03:06   0:00 [kblockd/0]
root         4  0.0  0.0      0     0 ?        S<   03:06   0:00 [ksoftirqd/0]
root      3279  0.0  0.0      0     0 ?        S<   03:06   0:00 [ipw2200/0]
root      3277  0.0  0.0      0     0 ?        S<   03:06   0:00 [pccardd]
root      3250  0.0  0.0      0     0 ?        S<   03:06   0:00 [pccardd]
root      3049  0.0  0.0      0     0 ?        S<   03:06   0:00 [kpsmoused]
root         3  0.0  0.0      0     0 ?        S<   03:06   0:00 [migration/0]
root      2461  0.0  0.0      0     0 ?        S<   03:06   0:00 [kjournald]
root      2281  0.0  0.0      0     0 ?        S<   03:06   0:00 [knodemgrd_0]
root      2141  0.0  0.0      0     0 ?        S<   03:06   0:00 [scsi_eh_1]
root      2139  0.0  0.0      0     0 ?        S<   03:06   0:00 [scsi_eh_0]
root         2  0.0  0.0      0     0 ?        S<   03:06   0:00 [kthreadd]
root       199  0.0  0.0      0     0 ?        S<   03:06   0:00 [aio/0]
root       158  0.0  0.0      0     0 ?        S<   03:06   0:00 [kswapd0]
root       157  0.0  0.0      0     0 ?        S    03:06   0:00 [pdflush]
root       156  0.0  0.0      0     0 ?        S    03:06   0:00 [pdflush]
root      1536  0.0  0.0      0     0 ?        S<   03:06   0:00 [khpsbpkt]
root      1533  0.0  0.0      0     0 ?        S<   03:06   0:00 [ata_aux]
root      1527  0.0  0.0      0     0 ?        S<   03:06   0:00 [ata/0]
root      1503  0.0  0.0      0     0 ?        S<   03:06   0:00 [khubd]
root      1500  0.0  0.0      0     0 ?        S<   03:06   0:00 [ksuspend_usbd]
root       125  0.0  0.0      0     0 ?        S<   03:06   0:00 [kseriod]
dhcp      5774  0.0  0.0   2436   716 ?        S<s  03:07   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
daemon    5395  0.0  0.0   1984   424 ?        Ss   03:06   0:00 /usr/sbin/atd
avahi     4961  0.0  0.0   2760   464 ?        Ss   03:06   0:00 avahi-daemon: chroot helper
104       5694  0.0  0.0   1964   756 ?        S<s  03:07   0:00 avahi-autoipd: [eth0] bound 169.254.9.195
```

any help much appreciated,

Chris

---

### Post by Archmage on 2008-09-10
> **csmeder said:**
> First question: What does 
```
memory: 
40% in use by programs 
55% in use as cache
``` 

mean?

That 40% of your memory had been used by the programs. (All that is runing) 55% is used by the system for caching purpose (it loads things already in memory that it thinks that you need later).

---

### Post by chrisccoulson on 2008-09-10
What does the output of:
```
free -m
```
look like after you boot?

---

### Post by public_void on 2008-09-10
Linux uses more memory to cache programs and files that you might need. Therefore you can quickly access those program when necessary. There is no point leaving memory free and wasting it.

---

### Post by jerome1232 on 2008-09-10
Yup Yup, in addition what's used for cache is dropped in favor for applications should they need more memory.

So If you opened up another instance of firefox cache would be dropped to make room for firefox.

---

### Post by csmeder on 2008-09-11
Archmage, public_void and jerome thank you. I understand now.


chrisccoulson thank you. I ran it after I booted (and opened firefox):
```
 free -m
             total       used       free     shared    buffers     cached
Mem:           748        735         12          0         34        213
-/+ buffers/cache:        487        260
Swap:         1098         37       1060
```

522mb seems like a lot of memory to be used up just by the core system and firefox?

The reason I care, is that if I start watching flash movies in firefox, the system quickly runs out of memory. It seems like start up and firefox should only take, what? 120mb? What is all this memory being used for?

A few months ago I had only 512mb of ram, and often the system would stay under 400mb, even with firefox and eclipse running, now when I start up the system is eating like 400-500 mb of ram. Is it the upgrade to 8.04?

PS I am not running compiz or anything special, as you can see from my ps aux print out.

Thanks,

Chris

edit: I redid free -m with a clean boot and still 500mb is being used?
```
 free -m
             total       used       free     shared    buffers     cached
Mem:           748        738          9          0        285        230
-/+ buffers/cache:        222        525
Swap:         1098          0       1098

```

---

