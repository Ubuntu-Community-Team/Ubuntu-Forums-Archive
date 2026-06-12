---
title: "some X applications (not all) are very slow"
date: 2008-08-23
forum: General Help
---

### Post by margot on 2008-08-23
I'm running Ubuntu 8.04, Kernel 2.6.24-19 and xfce-4 on a Dell XEON Desktop with 2G RAM.

Some applications are *very* slow to launch; others are not. After they launch they tend to freeze and are generally slow to respond. For example evince, gnumeric and firefox is slow. On the other hand: command-line applications, emacs, abiword and ghostview are still fast. I don't know what these have in common that could explain the problem.

Some background:

I switched from Red Hat about two weeks ago: things were fine except sound didn't work. In the course of trying to fix sound, something happened: At first I got a message saying I was no longer owner of $HOME.dmrc. I fixed permissions, but since then I have this other problem.

Any ideas how I can at least diagnose where the problem lies?

---

### Post by LateNiteTV on 2008-08-23
open one of the apps that is usually slow, then run:
```
ps aux
```
and post the output.

---

### Post by margot on 2008-08-23
Thanks. I can post this on Monday. But I can tell you, the process does not start eating up a lot of memory or CPU (I watched on 'top' while launching these applications). Is that what you were looking for?

---

### Post by margot on 2008-08-25
This is the output from 
ps aux 
after
firefox&

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   4020   888 ?        Ss   Aug21   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Aug21   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Aug21   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Aug21   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Aug21   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   Aug21   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   Aug21   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   Aug21   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   Aug21   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   Aug21   0:00 [khelper]
root        44  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kblockd/0]
root        45  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kblockd/1]
root        48  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kacpid]
root        49  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kacpi_notify]
root       150  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kseriod]
root       198  0.0  0.0      0     0 ?        S    Aug21   0:00 [pdflush]
root       199  0.0  0.0      0     0 ?        S    Aug21   0:00 [pdflush]
root       200  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kswapd0]
root       243  0.0  0.0      0     0 ?        S<   Aug21   0:00 [aio/0]
root       244  0.0  0.0      0     0 ?        S<   Aug21   0:00 [aio/1]
root      1565  0.0  0.0      0     0 ?        S<   Aug21   0:00 [ksuspend_usbd]
root      1578  0.0  0.0      0     0 ?        S<   Aug21   0:00 [khubd]
root      1594  0.0  0.0      0     0 ?        S<   Aug21   0:00 [khpsbpkt]
root      1606  0.0  0.0      0     0 ?        S<   Aug21   0:04 [ata/0]
root      1625  0.0  0.0      0     0 ?        S<   Aug21   0:04 [ata/1]
root      1626  0.0  0.0      0     0 ?        S<   Aug21   0:00 [ata_aux]
root      2362  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_0]
root      2526  0.0  0.0      0     0 ?        S<   Aug21   0:00 [knodemgrd_0]
root      2539  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_1]
root      2540  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_2]
root      2541  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_3]
root      2542  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_4]
root      2543  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_5]
root      2544  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_6]
root      2579  0.0  0.0      0     0 ?        S<   Aug21   0:14 [scsi_eh_7]
root      2580  0.0  0.0      0     0 ?        S<   Aug21   0:00 [scsi_eh_8]
root      2734  0.0  0.0      0     0 ?        S<   Aug21   0:01 [kjournald]
root      2917  0.0  0.0  17200  1312 ?        S<s  Aug21   0:00 /sbin/udevd --daemon
root      3297  0.0  0.0      0     0 ?        S<   Aug21   0:01 [edac-poller]
root      3411  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kpsmoused]
daemon    3920  0.0  0.0   8084   484 ?        S<s  Aug21   0:00 /sbin/portmap
root      4530  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kjournald]
root      4956  0.0  0.0   3864   596 tty4     Ss+  Aug21   0:00 /sbin/getty 38400 tty4
root      4957  0.0  0.0   3864   596 tty5     Ss+  Aug21   0:00 /sbin/getty 38400 tty5
root      4959  0.0  0.0   3864   592 tty2     Ss+  Aug21   0:00 /sbin/getty 38400 tty2
root      4961  0.0  0.0   3864   592 tty3     Ss+  Aug21   0:00 /sbin/getty 38400 tty3
root      4963  0.0  0.0   3864   596 tty6     Ss+  Aug21   0:00 /sbin/getty 38400 tty6
root      5143  0.0  0.0  13076  1760 ?        Ss   Aug21   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5180  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kondemand/0]
root      5181  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kondemand/1]
syslog    5259  0.0  0.0  12296   756 ?        Ss   Aug21   0:00 /sbin/syslogd -u syslog
root      5312  0.0  0.0   8132   592 ?        S    Aug21   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5314  0.0  0.1   7108  3884 ?        Ss   Aug21   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5337  0.0  0.0  21468  1296 ?        Ss   Aug21   0:00 /usr/bin/dbus-daemon --system
root      5353  0.0  0.1  44336  2120 ?        Ss   Aug21   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5367  0.0  0.0  28356  1288 ?        Ss   Aug21   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      5380  0.0  0.0  35192  1220 ?        Ss   Aug21   0:00 /usr/bin/system-tools-backends
avahi     5447  0.0  0.0  29712  1652 ?        Ss   Aug21   0:00 avahi-daemon: running [monotone.local]
avahi     5448  0.0  0.0  29580   504 ?        Ss   Aug21   0:00 avahi-daemon: chroot helper
root      5479  0.0  0.1  72444  2780 ?        Ss   Aug21   0:00 /usr/sbin/cupsd
root      5519  0.0  0.0 131344   988 ?        Ssl  Aug21   0:00 /usr/sbin/nscd
root      5666  0.0  0.0   6272   804 ?        Ss   Aug21   0:01 /usr/sbin/dhcdbd --system
111       5685  0.0  0.2  34348  4380 ?        Ss   Aug21   0:01 /usr/sbin/hald
root      5688  0.0  0.1  35032  2460 ?        Ssl  Aug21   0:00 /usr/sbin/console-kit-daemon
root      5689  0.0  0.0  22048  1296 ?        S    Aug21   0:00 hald-runner
root      5773  0.0  0.0  24156  1284 ?        S    Aug21   0:00 hald-addon-input: Listening on /dev/input/event2 /dev/input/event4 /dev/input/event5
111       5776  0.0  0.0   8676   808 ?        S    Aug21   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5794  0.0  0.0  24156  1276 ?        S    Aug21   0:02 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5797  0.0  0.0  24156  1280 ?        S    Aug21   0:06 hald-addon-storage: polling /dev/scd1 (every 2 sec)
root      5820  0.0  0.0  17760  1300 ?        Ss   Aug21   0:00 /usr/sbin/hcid -x -s
root      5827  0.0  0.0      0     0 ?        S<   Aug21   0:00 [btaddconn]
root      5828  0.0  0.0      0     0 ?        S<   Aug21   0:00 [btdelconn]
root      5838  0.0  0.0  17580  1184 ?        S    Aug21   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5839  0.0  0.0  17656  1396 ?        S    Aug21   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5844  0.0  0.0      0     0 ?        S<   Aug21   0:00 [krfcommd]
root      5884  0.0  0.0 110328  1872 ?        Ss   Aug21   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      5887  0.0  0.1 129416  3492 ?        S    Aug21   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
daemon    5954  0.0  0.0   8432   396 ?        Ss   Aug21   0:00 /usr/sbin/atd
root      5968  0.0  0.0  10408   768 ?        Ss   Aug21   0:00 /usr/sbin/cron
root      6048  0.0  0.0  46124  1304 tty1     Ss   Aug21   0:00 /bin/login --     
root      6246  0.0  0.0      0     0 ?        S<   Aug21   0:00 [rpciod/0]
root      6247  0.0  0.0      0     0 ?        S<   Aug21   0:00 [rpciod/1]
root      6385  0.0  0.0  44856  1132 ?        Ss   Aug21   0:00 /usr/sbin/sshd
fede      7878  0.0  0.0  43388  1412 ?        S    Aug22   0:00 gnome-keyring-daemon
fede      8619  0.0  0.0  43388  1416 ?        S    Aug22   0:00 gnome-keyring-daemon
fede      8743  0.0  0.1  11196  2148 tty1     S+   Aug22   0:00 -bash
root      8924  0.0  1.6 106496 34904 tty7     SLs+ Aug22   0:30 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
fede     12888  0.0  0.2  35388  5548 ?        S    09:04   0:00 /usr/lib/libgconf2-4/gconfd-2 9
fede     12890  0.0  0.0  43536  2004 ?        S    09:04   0:00 /usr/bin/gnome-keyring-daemon -d --login
fede     12892  0.0  0.0   3944   592 ?        Ss   09:04   0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
fede     12971  0.0  0.3 206468  7500 ?        Ss   09:04   0:00 /usr/bin/seahorse-agent --execute startxfce4
fede     12979  0.0  0.0  17560   656 ?        S    09:04   0:00 /usr/bin/dbus-launch --sh-syntax --exit-with-session
fede     12980  0.0  0.0  13192   884 ?        Ss   09:04   0:00 /usr/bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
fede     12983  0.0  0.0  13420  1204 ?        S    09:04   0:00 /usr/lib/gamin/gam_server
fede     12993  0.0  0.0  33600   664 ?        Ss   09:04   0:00 /usr/bin/ssh-agent -s
fede     12995  0.0  0.6 153860 12600 ?        Sl   09:04   0:00 /usr/bin/xfce4-session
fede     12996  0.0  0.1 127900  3944 ?        Ss   09:04   0:00 gnome-screensaver
fede     13001  0.0  0.5 235724 11440 ?        Ss   09:04   0:00 xfce-mcs-manager
fede     13003  0.0  0.0  43388  1412 ?        S    09:04   0:00 gnome-keyring-daemon
fede     13004  0.0  0.6 138116 13596 ?        S    09:04   0:00 xfwm4 --sm-client-id 1183d7178c000121873891300000226640000 --display :0.0
fede     13006  0.0  0.2 131956  5596 ?        S    09:04   0:00 Thunar --sm-client-id 1183d7178c000121873891300000226640002 --daemon
fede     13007  0.0  0.6 156580 14248 ?        S    09:04   0:00 xfdesktop --sm-client-id 1183d7178c000121873891400000226640003 --display :0.0
fede     13008  0.0  0.1  60312  4096 ?        S    09:04   0:00 xterm -xtsessionID 1183d7178c000121874063700000231010003
fede     13009  0.0  0.1  60396  3936 ?        S    09:04   0:00 xterm -xtsessionID 1183d7178c000121873891500000226640004 -geometry 80x120-1+1
fede     13010  0.0  1.0 213532 20644 ?        S    09:04   0:00 update-notifier --sm-config-prefix /update-notifier-eCGk4h/ --sm-client-id 1183d7178c000121873891500000226640005 --screen 0
fede     13011  0.0  0.1  11176  2148 pts/0    Ss   09:04   0:00 bash
fede     13012  0.0  0.1  11168  2092 pts/1    Ss+  09:04   0:00 bash
fede     13016  0.0  0.4 209284  8908 ?        Ss   09:04   0:00 gnome-power-manager --sm-config-prefix /gnome-power-manager-rQmG5h/ --sm-client-id 1183d7178c000121873891500000226640006 --screen 0
fede     13020  0.0  0.1  60404  4020 ?        Ss   09:04   0:00 xterm -geometry 80x120-1+1
fede     13029  0.0  0.9 207888 20028 ?        Ss   09:04   0:00 nm-applet --sm-disable
fede     13031  0.0  0.7 194336 16416 ?        Ss   09:04   0:00 python /usr/share/system-config-printer/applet.py
fede     13035  0.0  0.5 136072 10904 ?        SNsl 09:04   0:00 trackerd
fede     13037  0.0  0.3 115672  6256 ?        Ss   09:04   0:00 tracker-applet
fede     13038  0.0  0.2 181204  5208 ?        Ss   09:04   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
fede     13050  0.0  0.1  11176  2140 pts/2    Ss+  09:04   0:00 bash
fede     13055  0.0  0.1  55884  3308 pts/0    S    09:04   0:00 xterm
fede     13056  0.0  0.0   9904  1932 pts/3    Ss   09:04   0:00 bash
fede     13058  0.0  0.1  40624  2452 pts/3    S+   09:04   0:00 ssh thebes
fede     13092  0.0  0.2  24228  4492 pts/2    S    09:09   0:00 /usr/bin/perl -w /usr/bin/xdvi convex.dvi
fede     13095  0.0  0.3  54880  7484 pts/2    S    09:09   0:00 xdvi.bin -name xdvi convex.dvi
fede     13096  0.1  0.7  79448 16368 pts/2    S    09:10   0:00 emacs convex.tex
fede     13117  4.2  2.1 406268 44056 pts/0    Sl   09:19   0:00 /usr/lib/firefox-3.0.1/firefox
fede     13125  0.0  0.0   6884   944 pts/0    R+   09:19   0:00 ps aux

---

### Post by LateNiteTV on 2008-08-26
sorry, i meant post the output of "top"... makes it easier to read. and please use the code tags.

---

### Post by margot on 2008-08-26
Here's something weird: adding

ifconfig lo 127.0.0.1

to /etc/rc.local

fixed the problem. I have no idea why! I just followed the thread

[http://ubuntuforums.org/showthread.p...=xrdb+ifconfig](http://ubuntuforums.org/showthread.p...=xrdb+ifconfig)

on a hunch. I have *no* idea why this worked.

Thanks for your help: I guess now posting output from top doesn't make sense; but any idea what may have happened ?

---

