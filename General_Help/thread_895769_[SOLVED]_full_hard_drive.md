---
title: "[SOLVED] full hard drive"
date: 2008-08-20
forum: General Help
---

### Post by afbase on 2008-08-20
It seems my Ext3 FS is full and it won't go down from 100% full.

```
clinton@clinton-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8            139644496 138835404         0 100% /
varrun                 1687500       116   1687384   1% /var/run
varlock                1687500         0   1687500   0% /var/lock
udev                   1687500        76   1687424   1% /dev
devshm                 1687500        12   1687488   1% /dev/shm
lrm                    1687500     39760   1647740   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7               241116     61009    167659  27% /boot
overflow                  1024        24      1000   3% /tmp
gvfs-fuse-daemon     139644496 138835404         0 100% /home/clinton/.gvfs

```

this df command was run when i deleted at least 6 gigs of old college documents, uninstalled 200+ megs of latex crap, and other stuff from synaptic, etc., etc..  It seems that whatever I delete, it shows that the disk is still full.  

I used the disk usage analyzer.  It suggests that i've only used roughly 25 gigs out of the 140 gigs from /dev/sda8.

I have two ntfs partitions on the drive for vista and XP.  Both are 54 gig partitions.  

Any ideas?

---

### Post by LateNiteTV on 2008-08-20
do you get any errors when you try to write to that partition?

---

### Post by Elfy on 2008-08-20
Have you emptied the trash - and roots?

---

### Post by dexter.deepak on 2008-08-20
this removes all your downloaded softwares through apt-get :
```
sudo apt-get clean
```
in the past it has often helped me get more space.

---

### Post by afbase on 2008-08-20
> **dexter.deepak said:**
> this removes all your downloaded softwares through apt-get :
```
sudo apt-get clean
```
in the past it has often helped me get more space.

I've tried that, i've cleaned up the dpkg, I've checked my trash and the root trash (and cleaned them).  Something isn't adding up.   How does df show 100% full and yet i've disk usage analyzer show i've only used 25 gigs?

Could a process hog memory?

I figure i'll just post my running processes to see if that helps any:

```
clinton@clinton-laptop:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2904  1684 ?        Ss   10:51   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:51   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:51   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   10:51   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:51   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:51   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   10:51   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   10:51   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   10:51   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   10:51   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   10:51   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   10:51   0:00 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<   10:51   0:00 [kblockd/1]
root        50  0.0  0.0      0     0 ?        S<   10:51   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   10:51   0:00 [kacpi_notify]
root       140  0.0  0.0      0     0 ?        S<   10:51   0:00 [kseriod]
root       182  0.0  0.0      0     0 ?        S    10:51   0:00 [pdflush]
root       183  0.0  0.0      0     0 ?        S    10:51   0:00 [pdflush]
root       184  0.0  0.0      0     0 ?        S<   10:51   0:00 [kswapd0]
root       225  0.0  0.0      0     0 ?        S<   10:51   0:00 [aio/0]
root       226  0.0  0.0      0     0 ?        S<   10:51   0:00 [aio/1]
root      1590  0.0  0.0      0     0 ?        S<   10:51   0:00 [ksuspend_usbd]
root      1593  0.0  0.0      0     0 ?        S<   10:51   0:00 [khubd]
root      1596  0.0  0.0      0     0 ?        S<   10:51   0:00 [khpsbpkt]
root      1609  0.0  0.0      0     0 ?        S<   10:51   0:00 [knodemgrd_0]
root      1616  0.0  0.0      0     0 ?        S<   10:51   0:00 [ata/0]
root      1625  0.0  0.0      0     0 ?        S<   10:51   0:00 [ata/1]
root      1630  0.0  0.0      0     0 ?        S<   10:51   0:00 [ata_aux]
root      2369  0.0  0.0      0     0 ?        S<   10:51   0:00 [scsi_eh_0]
root      2371  0.0  0.0      0     0 ?        S<   10:51   0:01 [scsi_eh_1]
root      2807  0.0  0.0      0     0 ?        S<   10:51   0:00 [kjournald]
root      3047  0.0  0.0   2600  1068 ?        S<s  10:52   0:00 /sbin/udevd --daemon
root      3318  0.0  0.0      0     0 ?        S<   10:52   0:00 [kpsmoused]
root      3456  0.0  0.0      0     0 ?        S<   10:52   0:00 [kmmcd]
root      3626  0.0  0.0      0     0 ?        S<   10:52   0:00 [btaddconn]
root      3628  0.0  0.0      0     0 ?        S<   10:52   0:00 [btdelconn]
root      3754  0.9  0.0      0     0 ?        R<   10:52   0:42 [b43]
root      4780  0.0  0.0      0     0 ?        S<   10:52   0:00 [kjournald]
root      5070  0.0  0.0   1776   516 tty4     Ss+  10:52   0:00 /sbin/getty 38400 tty4
root      5071  0.0  0.0   1776   512 tty5     Ss+  10:52   0:00 /sbin/getty 38400 tty5
root      5073  0.0  0.0   1776   516 tty2     Ss+  10:52   0:00 /sbin/getty 38400 tty2
root      5075  0.0  0.0   1776   512 tty3     Ss+  10:52   0:00 /sbin/getty 38400 tty3
root      5077  0.0  0.0   1776   516 tty6     Ss+  10:52   0:00 /sbin/getty 38400 tty6
root      5261  0.0  0.0   2528  1360 ?        Ss   10:52   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5304  0.0  0.0      0     0 ?        S<   10:52   0:00 [kondemand/0]
root      5305  0.0  0.0      0     0 ?        S<   10:52   0:00 [kondemand/1]
syslog    5379  0.0  0.0   2008   652 ?        Ss   10:52   0:00 /sbin/syslogd -u syslog
root      5434  0.0  0.0   1936   524 ?        S    10:52   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5436  0.0  0.0   3668  2488 ?        Ss   10:52   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5458  0.0  0.0   3012  1400 ?        Ss   10:52   0:00 /usr/bin/dbus-daemon --system
root      5474  0.0  0.0  29516  2324 ?        Ssl  10:52   0:02 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5488  0.0  0.0   3652  1344 ?        Ss   10:52   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      5501  0.0  0.0   4260  1148 ?        Ss   10:52   0:00 /usr/bin/system-tools-backends
avahi     5521  0.0  0.0   2836  1436 ?        Ss   10:52   0:00 avahi-daemon: running [clinton-laptop.local]
avahi     5522  0.0  0.0   2836   476 ?        Ss   10:52   0:00 avahi-daemon: chroot helper
root      5551  0.0  0.0   4144  1620 ?        Ss   10:52   0:00 /usr/sbin/atieventsd
root      5578  0.0  0.0   6888  2476 ?        Ss   10:52   0:00 /usr/sbin/cupsd
root      5642  0.0  0.0   8276  1312 ?        Ss   10:52   0:00 /usr/sbin/winbindd
root      5647  0.0  0.0   8276  1096 ?        S    10:52   0:00 /usr/sbin/winbindd
root      5692  0.0  0.0   2080   884 ?        Ss   10:52   0:00 /usr/sbin/dhcdbd --system
111       5711  0.0  0.1   6484  4408 ?        Ss   10:52   0:02 /usr/sbin/hald
root      5714  0.0  0.0   8008  2432 ?        Ssl  10:52   0:00 /usr/sbin/console-kit-daemon
root      5715  0.0  0.0   3460  1184 ?        S    10:52   0:00 hald-runner
root      5789  0.0  0.0   5280  2120 ?        S    10:52   0:00 /usr/lib/hal/hald-addon-dell-backlight
root      5790  0.0  0.0   3524  1156 ?        S    10:52   0:00 hald-addon-input: Listening on /dev/input/event10 /dev/input/event12 /dev/input/event11 /dev/input/event3 /dev/i
root      5801  0.0  0.0   3536  1232 ?        S    10:52   0:00 /usr/lib/hal/hald-addon-cpufreq
111       5802  0.0  0.0   2276   892 ?        S    10:52   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5824  0.0  0.0   3528  1156 ?        S    10:52   0:01 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5855  0.0  0.0      0     0 ?        S<   10:52   0:00 [ipolldevd]
root      5856  0.0  0.0   3260  1344 ?        Ss   10:52   0:00 /usr/sbin/hcid -x -s
root      5867  0.0  0.0   3172  1312 ?        S    10:52   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5875  0.0  0.0   3108  1112 ?        S    10:52   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5883  0.0  0.0   2008   480 ?        Ss   10:52   0:00 /usr/bin/hidd --master --server
root      5888  0.0  0.0      0     0 ?        S<   10:52   0:00 [krfcommd]
root      5922  0.0  0.0  14208  1640 ?        Ss   10:52   0:00 /usr/sbin/gdm
root      5929  0.0  0.0  14672  3060 ?        S    10:52   0:00 /usr/sbin/gdm
root      5936  5.5  4.3 157020 145480 tty7    Ss+  10:52   3:55 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daemon    5964  0.0  0.0   2056   440 ?        Ss   10:52   0:00 /usr/sbin/atd
root      5981  0.0  0.0   2180   900 ?        Ss   10:52   0:00 /usr/sbin/cron
root      6059  0.0  0.0  10488  2392 ?        Ss   10:52   0:00 /usr/sbin/apache2 -k start
www-data  6060  0.0  0.0  10488  1836 ?        S    10:52   0:00 /usr/sbin/apache2 -k start
www-data  6062  0.0  0.0  10488  1836 ?        S    10:52   0:00 /usr/sbin/apache2 -k start
www-data  6064  0.0  0.0  10488  1836 ?        S    10:52   0:00 /usr/sbin/apache2 -k start
www-data  6065  0.0  0.0  10488  1836 ?        S    10:52   0:00 /usr/sbin/apache2 -k start
www-data  6066  0.0  0.0  10488  1836 ?        S    10:52   0:00 /usr/sbin/apache2 -k start
root      6139  0.0  0.0   1776   516 tty1     Ss+  10:52   0:00 /sbin/getty 38400 tty1
root      6179  0.0  4.3 157020 145480 tty7    S+   10:52   0:00 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
clinton   6204  0.0  0.1   7388  4436 ?        S    10:52   0:01 /usr/lib/libgconf2-4/gconfd-2 4
clinton   6206  0.0  0.0  23928  2328 ?        S    10:52   0:00 /usr/bin/gnome-keyring-daemon -d --login
clinton   6207  0.0  0.2  28716  6924 ?        Ssl  10:52   0:00 x-session-manager
clinton   6263  0.0  0.2  23196  7556 ?        Ss   10:52   0:00 /usr/bin/seahorse-agent --execute x-session-manager
clinton   6267  0.0  0.0   2908  1280 ?        Ss   10:52   0:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
clinton   6268  0.0  0.2  40980 10060 ?        Sl   10:52   0:01 gnome-settings-daemon
clinton   6272  0.2  0.1  29972  4508 ?        Sl   10:52   0:12 /usr/bin/pulseaudio --log-target=syslog
clinton   6282  0.0  0.0   5908  2284 ?        S    10:52   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
clinton   6291  0.1  0.0  15052  2744 ?        Ss   10:52   0:05 gnome-screensaver
clinton   6297  0.0  0.0  41272  3260 ?        Ssl  10:52   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=24
clinton   6301  0.0  0.0   1832   540 ?        S    10:52   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
clinton   6303  0.0  0.2  18148  6768 ?        S    10:52   0:02 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
clinton   6305  0.4  0.6  48604 23404 ?        S    10:52   0:20 gnome-panel --sm-client-id default1
clinton   6307  0.3  1.0  85520 34524 ?        S    10:52   0:13 nautilus --no-default-window --sm-client-id default2
clinton   6334  0.0  0.0   5532  2168 ?        S    10:52   0:00 /usr/lib/gvfs/gvfsd
clinton   6376  0.6  0.5  24424 17392 ?        S    10:52   0:26 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id default0 core ccp
clinton   6380  0.0  0.2  22452 10056 ?        S    10:52   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=23
clinton   6382  0.1  0.1  39736  3700 ?        Ssl  10:52   0:04 /usr/lib/gvfs//gvfs-fuse-daemon /home/clinton/.gvfs
clinton   6388  0.0  0.0  22196  2676 ?        S    10:52   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
clinton   6400  0.0  0.0   5532  2164 ?        S    10:52   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
clinton   6406  0.0  0.4  44276 15580 ?        Sl   10:52   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=24
clinton   6408  0.0  0.4  25644 13600 ?        S    10:52   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Fa
clinton   6413  0.0  0.0   1832   484 ?        Ss   10:52   0:00 /bin/sh -c /usr/bin/compiz-decorator
clinton   6414  0.0  0.0   1832   508 ?        S    10:52   0:00 /bin/sh /usr/bin/compiz-decorator
clinton   6416  0.0  0.3  21024 11592 ?        S    10:52   0:01 /usr/bin/gtk-window-decorator
clinton   6437  0.0  0.0   1832   484 ?        Ss   10:53   0:00 /bin/sh -c gnome-terminal
clinton   6438  0.0  0.6  75580 22244 ?        Rl   10:53   0:01 gnome-terminal
clinton   6440  0.0  0.0   3016   860 ?        S    10:53   0:00 gnome-pty-helper
clinton   6441  0.0  0.1   6064  3428 pts/0    Ss+  10:53   0:00 bash
clinton   6498  0.0  0.1   6120  3484 pts/1    Ss   10:54   0:00 bash
clinton   6526  0.0  0.0   1832   516 ?        S    10:54   0:00 /bin/sh /home/clinton/.mozilla/firefox/firefox
clinton   6529  0.0  0.0   1832   528 ?        S    10:54   0:00 /bin/sh /home/clinton/.mozilla/firefox/run-mozilla.sh /home/clinton/.mozilla/firefox/firefox-bin
clinton   6534 13.2  5.7 429644 192720 ?       Sl   10:54   9:06 /home/clinton/.mozilla/firefox/firefox-bin
clinton   6574  0.0  0.2  18596  8756 ?        S    10:54   0:00 bluetooth-applet --singleton
clinton   6576  0.0  0.4  25416 13996 ?        S    10:54   0:00 update-notifier
clinton   6582  0.0  0.0   3052   424 ?        Ss   10:54   0:00 syndaemon -i 1 -d -t -K
clinton   6584  0.0  0.1  15460  5524 ?        S    10:54   0:00 tracker-applet
clinton   6586  0.0  0.3  63004 10152 ?        Sl   10:54   0:00 /usr/lib/evolution/2.22/evolution-alarm-notify
clinton   6590  0.0  0.0   4880  1820 ?        S    10:54   0:00 /usr/bin/obex-data-server --no-daemon
clinton   6591  0.0  0.3  31660 10440 ?        SNl  10:54   0:00 trackerd
clinton   6594  0.0  0.1  20536  4932 ?        Ss   10:54   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
clinton   6596  0.0  0.3  23288 13468 ?        S    10:54   0:01 /usr/lib/notification-daemon/notification-daemon
clinton   6597  0.1  0.4  26636 14916 ?        S    10:54   0:04 nm-applet --sm-disable
clinton   6598  0.0  0.3  24720 12172 ?        S    10:54   0:00 python /usr/share/system-config-printer/applet.py
clinton   6599  0.0  0.2  23464  8772 ?        Ss   10:54   0:00 gnome-power-manager
clinton   6614  0.0  0.2  39420  9312 ?        Sl   10:54   0:00 /usr/lib/evolution/2.22/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_
clinton   6640  0.0  0.1   8944  3488 ?        S    10:54   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
clinton   6667  0.0  0.2  68816  7016 ?        Sl   10:54   0:00 /usr/lib/evolution/evolution-data-server-2.22 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.
root      6697  0.0  0.0   3940  1516 ?        S    10:54   0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
dhcp      6744  0.0  0.0   2512  1164 ?        S    10:54   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -q -e dhc_dbus=31 -d
clinton   7056  0.9  0.8  40276 27964 ?        S    11:02   0:35 baobab
clinton   9015  0.5  1.1  99692 38900 ?        Sl   11:56   0:02 rhythmbox
clinton   9291  0.0  0.0   2716  1012 pts/1    R+   12:02   0:00 ps -aux

```

---

### Post by bodhi.zazen on 2008-08-20
> **forestpixie said:**
> Have you emptied the trash - and roots?
 

Empty ~/.Trash and /root/.Trash

---

### Post by Elfy on 2008-08-20
Memory and disk space aren't connected, when you used baobab where was it set to look - you need to view the whole filesystem - scan filesystem.

When you checked the trashes - did you view hidden files.

Edit - root trash is in /home/.Trash-0 in hardy

---

### Post by afbase on 2008-08-20
> **bodhi.zazen said:**
> Empty ~/.Trash and /root/.Trash

...ok so in gnome, i've clicked on the little blue trash can and emptied the trash.  I've also ctrl+h to look for the Trash folder in ~ and in /root.  They're not there.  

Is there something that i'm missing?

---

### Post by afbase on 2008-08-20
> **forestpixie said:**
> Memory and disk space aren't connected, when you used baobab where was it set to look - you need to view the whole filesystem - scan filesystem.

When you checked the trashes - did you view hidden files.

Edit - root trash is in /home/.Trash-0 in hardy

i scanned the filesystem.  I'd love to send you a screenshot, but since my disk is 'full' i can't save anything.

-edit
It reads that i've only used 25 gigs on /

/home has 15 gigs /usr has 7 gigs, and everything else encompasses the other 3 remaining gigs.  and yes, this a 140 gig partition, yet df still reads 100% used

---

### Post by Elfy on 2008-08-20
Did you check root trash in home/.Trash-0 - no need for a screenshot I believe you :)

```
gksudo nautilus /home/.Trash-0
```

Doing a bit of digging - back in a bit...

---

### Post by afbase on 2008-08-20
> **forestpixie said:**
> Did you check root trash in home/.Trash-0 - no need for a screenshot I believe you :)

```
gksudo nautilus /home/.Trash-0
```

Doing a bit of digging - back in a bit...

```
Could not find "/home/.Trash-0"
```

---

### Post by Elfy on 2008-08-20
What version of ubuntu are you using? You did view hidden files I assume.

root trash is either where I've put it or where bodhi_zazen has.

---

### Post by afbase on 2008-08-20
> **forestpixie said:**
> What version of ubuntu are you using? You did view hidden files I assume.

root trash is either where I've put it or where bodhi_zazen has.

I'm using hardy heron.  With nautilus i've looked at /root /home for .Trash and .Trash-0.  These folders are missing.  I'm guessing this is a bad thing?

---

### Post by Elfy on 2008-08-20
There is no trash in /root in hardy they are both in /home, roots is at /home/.Trash-0 and yours is at ~/.local/share/Trash

I wonder if it's because you've no room that you can't get at the trashes in /home; I think I've seen a similar scenario with a full drive.

You could delete them from the command line, try without logging out first

```
rm -R /home/username/.local/share/Trash/*
```

Then to delete roots

```
sudo -i
cd /home/.Trash-0
```

Check the contents with 

```
cd /files
ls
```

and if ok delete

```
cd /home/.Trash-0
rm -R *
exit
```

If however you can't do it from within your logged in buntu you might have to reboot and then do it from a root prompt in recovery mode, the only difference being that you will not need to sudo -i , although I'm a bit concerned that you won't be able to log in again with a full drive.

---

### Post by afbase on 2008-08-20
> **forestpixie said:**
> There is no trash in /root in hardy they are both in /home, roots is at /home/.Trash-0 and yours is at ~/.local/share/Trash

I wonder if it's because you've no room that you can't get at the trashes in /home; I think I've seen a similar scenario with a full drive.

You could delete them from the command line, try without logging out first

```
rm -R /home/username/.local/share/Trash/*
```

Then to delete roots

```
sudo -i
cd /home/.Trash-0
```

Check the contents with 

```
cd /files
ls
```

and if ok delete

```
cd /home/.Trash-0
rm -R *
exit
```

If however you can't do it from within your logged in buntu you might have to reboot and then do it from a root prompt in recovery mode, the only difference being that you will not need to sudo -i , although I'm a bit concerned that you won't be able to log in again with a full drive.

I tried your second set of commands and i got an error.

```
root@clinton-laptop:~# cd /home/.Trash-0
-bash: cd: /home/.Trash-0: No such file or directory

```

I have already done the first set of instructions and I also df'ed.  this is what it showed.

```
clinton@clinton-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8            139644496 138390672         0 100% /
varrun                 1687500       124   1687376   1% /var/run
varlock                1687500         0   1687500   0% /var/lock
udev                   1687500        76   1687424   1% /dev
devshm                 1687500       588   1686912   1% /dev/shm
lrm                    1687500     39760   1647740   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7               241116     61009    167659  27% /boot
overflow                  1024        40       984   4% /tmp
gvfs-fuse-daemon     139644496 138390672         0 100% /home/clinton/.gvfs

```

I have no problem logging in and out of ubuntu, or restarting.  Could it be something other than the 'Trash'? ok well I have work in about an hour,  I won't be on until later.

---

### Post by Elfy on 2008-08-20
I'll have a think - be later now though. When you did delete the stuff you mention at the beginning did it do it properly?

Might be worth booting the livecd tocheck from there, but it is odd that deleteing 6Gb didn't change df -h - which is why I think it must be in trash still.

---

### Post by nc_jed on 2008-08-20
whatever you do, don't log out.  this happened to me recently (disk full, that is).  I logged out and couldn't log back in (couldn't create a session w/o some disk space).

---

### Post by Elfy on 2008-08-20
This is what I was concerned about. Not too sure where to go from here though...

---

### Post by mgmiller on 2008-08-20
In my Hardy, I have roots trash located in a different spot.  I start....
 ```
gksu nautilus
```

It will start with the file tree on the left in "Home Folder".

Click that to high lite it and then on the right you will see roots folders.  Now you do a ctrl-h to make the hidden files visible and you will see a folder called .Trash   that one can contain items as well.  Mine did and it surprised me.  I deleted all the files in that.

Back in your own home directory, I also had a hidden file called .Trash-marty which also contained some stuff.  Yours will have your name on it.

Finally, as noted above, your main trash is located in ~/.local/share/Trash


So, I had 3 trash bins and all of them had stuff in them.

---

### Post by bodhi.zazen on 2008-08-20
Re-reading the information, seems .gvfs is the problem.

See this thread : [http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)

---

### Post by Elfy on 2008-08-20
I'm not so sure that it is .gvfs, the thread is about baobab showing the disk to be bigger than it is - this is, I'm sure, about df -h reading the same as it did after over 6Gb of data was deleted, ie the data is still there - but doesn't appear in any of the trash. Of course I could be wrong...

---

### Post by bodhi.zazen on 2008-08-20
I am just pointing out :

> 
Filesystem                     1K-blocks         Used         Available Use% Mounted on

<clip>[FONT=Verdana]

[/FONT]gvfs-fuse-daemon     139644496 138390672         0             100% /home/clinton/.gvfs

---

### Post by afbase on 2008-08-21
> **forestpixie said:**
> I'm not so sure that it is .gvfs, the thread is about baobab showing the disk to be bigger than it is - this is, I'm sure, about df -h reading the same as it did after over 6Gb of data was deleted, ie the data is still there - but doesn't appear in any of the trash. Of course I could be wrong...

You might be onto something.  I'm not finding any /root/.Trash or /root/.local/share/Trash or any root trash.  I ran the following command:
```
clinton@clinton-laptop:~$ sudo find / -name "Trash"
/home/clinton/.local/share/Trash
/home/clinton/.evolution/mail/imap/clinton.bowen@IMAP.gmail.com/folders/[Gmail]/subfolders/Trash
```

I don't think i have a Trash folder for root or anywhere else in my file system. Will there ALWAYS be a Trash folder for root?  If so, is there a way to find these folders?

Also, I have a habit from windows computing.  I usually Shift+Delete things.  In windows, that permanently deletes files, skipping the whole recycle bin/Trash thing all together.  I now have a hunch that this might be the crux of the whole issue.  How is shift + delete different in ubuntu than windows?
---------
 
[QUOTE=bodhi.zazen]I am just pointing out :

Quote:
Filesystem 1K-blocks Used Available Use% Mounted on

<clip>

gvfs-fuse-daemon 139644496 138390672 0 100% /home/clinton/.gvfs [/QUOTE]

Thank you for that other thread you forwarded to me.  I just noticed that DUA was doubling my space.  I unchecked the .gvfs daemon thing as the post suggested.  Nothing has really changed though.  the home folder still has 15 gigs, the usr folder has 7, and everything else still occupies the remaining 3 gigs of data.

---

### Post by afbase on 2008-08-21
I stumbled on this thread: [http://ubuntuforums.org/showthread.php?t=856469](http://ubuntuforums.org/showthread.php?t=856469)

I test deleted something as root, and i notice a new folder, /root/.local/share/Trash  !!! 

I would try shift+deleting something, but at the moment I can't find anything that isn't important.  I just tried making a simple text file, but fate has it that i have a 'full hard drive' and thus, no simple text file can be made.:(

---

### Post by Elfy on 2008-08-21
Yes shift+delete works the same way.

---

### Post by amitkher on 2008-08-21
Here is one sure shot way of helping baobab figure out the real disk space of a partition, and leave out extraneous file-systems out of its calculations. I am using /boot as temporary space as this filesystem has some space left.

```

sudo mkdir /boot/copy
sudo mount --bind / /boot/copy

```

Now run baobab on /boot/copy instead of /. This is so that .gvfs and other stupid filesystems do not come into our way. /boot/copy contains only those files that are physically on the partition /dev/sda8.

If you want to remove /boot/copy, first unmount it then make sure it is unmounted (by df, or mount command) and then remove it. Better use rmdir instead of rm -r to remove it.
```

sudo umount /boot/copy
sudo mount | grep copy
sudo rmdir /boot/copy

```


It sounds dangerous, but rebooting might help. Sometimes a process does not get a chance to close its open files, and gets stuck without properly dying. Disk space of such files cannot be reclaimed, such space will not be reported as free by df but baobab cannot see these fles. Since we do not know which unreliable process you might be running, rebooting is the best option to properly shutdown all processes. Booting into a live-CD might help as you are unable to do basic stuff like creating simple text files etc.

---

### Post by amitkher on 2008-08-21
> **afbase said:**
> 
I would try shift+deleting something, but at the moment I can't find anything that isn't important.  I just tried making a simple text file, but fate has it that i have a 'full hard drive' and thus, no simple text file can be made.:(

Create your simple text file in /boot

---

### Post by afbase on 2008-08-21
> **amitkher said:**
> Here is one sure shot way of helping baobab figure out the real disk space of a partition, and leave out extraneous file-systems out of its calculations. I am using /boot as temporary space as this filesystem has some space left.

```

sudo mkdir /boot/copy
sudo mount --bind / /boot/copy

```

Now run baobab on /boot/copy instead of /. This is so that .gvfs and other stupid filesystems do not come into our way. /boot/copy contains only those files that are physically on the partition /dev/sda8.

If you want to remove /boot/copy, first unmount it then make sure it is unmounted (by df, or mount command) and then remove it. Better use rmdir instead of rm -r to remove it.
```

sudo umount /boot/copy
sudo mount | grep copy
sudo rmdir /boot/copy

```

The problem i get is that I cannot uncheck the / partition when i create /boot/copy in baobab.  It shows that i havee 266 gigs (133 in / and 133 in /boot/copy) instead of 133 gigs like it should  I did a filesystem scan anyway. It now shows 14.1 gigs in my home folder, usr folder has 9.2, everything else contain the remaining information of the total 23.8 gigs.  I tried making a screenshot and saving it to the boot partition.  It won't save!!!  i even tried:
```
sudo gnome-screenshot
```

No luck :confused:

**Deleting and shift deleting**

I took your other advice by saving a text file into the /boot partition.  I test deleted a file as root and found that it wound up in my /root/.local/share/Trash . I then made another text file, saved it in the /boot partition, then shift+deleted the file as root.  It wasn't found in my /root/.local/share/Trash, as it should be.  I then:
```
sudo find / -name "aaa.bbb"
```
And it wasn't anywhere on the filesystem.  

btw, my df has changed somewhat.

```
clinton@clinton-laptop:~$ df  -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             134G  120G  7.0G  95% /
varrun                1.7G  124K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   76K  1.7G   1% /dev
devshm                1.7G  432K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             236M   60M  164M  27% /boot
overflow              1.0M  452K  572K  45% /tmp
gvfs-fuse-daemon      134G  120G  7.0G  95% /home/clinton/.gvfs

```

once again, Baobab says / shows 23.8G as the size of / and df shows 120G  used on /.

---

### Post by Elfy on 2008-08-21
> I then made another text file, saved it in the /boot partition, then shift+deleted the file as root. It wasn't found in my /root/.local/share/Trash, as it should be.shift+delete doesn't send to trash it deletes.

It looks like the space you lost yesterday is now available then.

---

### Post by afbase on 2008-08-21
> **forestpixie said:**
> shift+delete doesn't send to trash it deletes.

It looks like the space you lost yesterday is now available then.

maybe some of it.  How can I account for the differences in sizes between DUA and df -h?  I am able to do a screen shot and i just did a screen shot of DUA.  here is a copy of my df -h:

```
clinton@clinton-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             134G  120G  7.0G  95% /
varrun                1.7G  120K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   76K  1.7G   1% /dev
devshm                1.7G   12K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             236M   60M  164M  27% /boot
gvfs-fuse-daemon      134G  120G  7.0G  95% /home/clinton/.gvfs

```**EDIT**
I guess my question is that why is there a difference in the usage in my DUA is only 23.9 gigs but /dev/sda8/ in DF says i've used 120 gigs?

---

### Post by Elfy on 2008-08-21
If baobab doesn't take into account the 5% ext3 keeps for journalling then they match generally

- df-h
134G  120G   7.0G  

-baobab
133.2G 119.5G 13.7G

approx 5% of the 134Gb is 6.5Gb, take that from the 13.7Gb that baobab says is free and you get about 7Gb free


Edit you could try to find one of the files you deleted yesterday with locate

```
sudo updatedb
locat filename
```

---

### Post by afbase on 2008-08-21
So if / is only 23.9 gigs large by DUA's screenshot, and DF says i've used 120 gigs, where did the other 96.1 gigs go?

---

### Post by Elfy on 2008-08-21
I don't know tbh, I've just run baobab and df-h on mine and they match; I rarely use baobab to look at files and prefer the terminal.

Do you have gparted installe d- look in there see what that says is the case, I'd be willing to bet it agrees with df-h.


I'm beginning to not see the wood from the trees here and don't think I'm going to able to add anything without going in circles...

---

### Post by unutbu on 2008-08-21
afbase, try running
```

gksu baobab
```

It appears that baobab only adds up the size of files that the user has permission to see.

---

### Post by afbase on 2008-08-21
> **unutbu said:**
> afbase, try running
```

gksu baobab
```It appears that baobab only adds up the size of files that the user has permission to see.
Crikey!!! I had 95 gigs of data in /var/archives

The largest files are Tar files that i'm guessing have backed up what files i had from each day for what seems to be the past month.  I'm having trouble cd'ing into the archives folder.  How do i CD into this with sudo permissions? I'd like to list the files to you guys.  but ya the only files in archives is Tar files and some md5 files. Is it ok to just delete this folder or just the Tar's?

---

### Post by unutbu on 2008-08-21
afbase, it appears that /var/archive is created by some backup script. I'm guessing your situation is the same as RyanGT's: [http://ubuntuforums.org/showthread.php?t=90977](http://ubuntuforums.org/showthread.php?t=90977)

How much you want to delete is up to you.
Deleting them won't hurt your system, you'll just lose the backups.

> 
How do i CD into this with sudo permissions? 


```

sudo -i   # gives you a root shell
cd /var/archive

```

Or you can use Nautilus:
```

gksu nautilus

```

---

### Post by afbase on 2008-08-21
> **unutbu said:**
> afbase, it appears that /var/archive is created by some backup script. I'm guessing your situation is the same as RyanGT's: [http://ubuntuforums.org/showthread.php?t=90977](http://ubuntuforums.org/showthread.php?t=90977)

How much you want to delete is up to you.
Deleting them won't hurt your system, you'll just lose the backups.



```

sudo -i   # gives you a root shell
cd /var/archive

```Or you can use Nautilus:
```

gksu nautilus

```
Thank You!!!:popcorn:

I guess i'll just have to investigate this backup thing more.  But shift+deleting the tar's in the /var/archives worked. I've found 95 of the 96 gigs I was looking for! I don't care about the one gig.  I'll just assume that pesky gig is just all the root's stuff. 

I have no idea where the back up script is.  I guess that will be another adventure.  :lolflag:

---

### Post by Elfy on 2008-08-22
Well - glad thats' done, I didn't know that baobab worked that way. Learnt something new as well today :)

If you come back could you mark thread solved please.

---

### Post by afbase on 2008-08-23
I searched synaptic to find that the program that seemed to be the suspect is backup-manager.  I read enough of the documentation to know that it uses /var/archives as a default setting to create backups for tar files.   I uninstalled backup-manager, so we'll see if that keeps things nice and tidy.  hopefully i'll remember to post back my FINAL conclusion on whether it was this program or not.

---

### Post by Elfy on 2008-08-23
It would certainly be nice to know what it was that caused it for you in the first place

---

### Post by afbase on 2008-08-25
well after uninstalling backup-manager, a few days of waiting, and checking /var/archives.   I believe that backup-manager was the culprit. :KS

Well I suppose this chapter is closed.

---

