---
title: "Can't update..."
date: 2008-11-04
forum: General Help
---

### Post by iamjfarrell on 2008-11-04
When I try to update using the terminal this is the feedback that I get.. What does this mean?

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by taurus on 2008-11-04
Do you have synaptic or apt running in the background?  Look at the output of this command to see if there is one.

```
ps -A
```

---

### Post by philinux on 2008-11-04
> **iamjfarrell said:**
> When I try to update using the terminal this is the feedback that I get.. What does this mean?

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Log out then log back in.

---

### Post by iamjfarrell on 2008-11-04
```

PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:03 migration/0
    4 ?        00:00:35 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:04 migration/1
    7 ?        00:02:31 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:10 events/0
   10 ?        00:00:14 events/1
   11 ?        00:00:00 khelper
   49 ?        00:00:00 kintegrityd/0
   50 ?        00:00:00 kintegrityd/1
   52 ?        00:00:13 kblockd/0
   53 ?        00:22:30 kblockd/1
   55 ?        00:00:00 kacpid
   56 ?        00:00:00 kacpi_notify
  164 ?        00:00:00 cqueue
  168 ?        00:00:00 kseriod
  220 ?        00:00:18 kswapd0
  266 ?        00:00:00 aio/0
  267 ?        00:00:00 aio/1
  521 ?        00:00:00 gvfsd-http
 1255 ?        00:00:00 ksuspend_usbd
 1261 ?        00:00:00 khubd
 1278 ?        00:00:03 ata/0
 1281 ?        00:01:57 ata/1
 1305 ?        00:00:00 ata_aux
 1310 ?        00:00:00 khpsbpkt
 1969 ?        00:00:37 soffice.bin
 2047 ?        00:03:55 scsi_eh_0
 2048 ?        00:00:00 scsi_eh_1
 2050 ?        00:00:00 scsi_eh_2
 2051 ?        00:00:00 scsi_eh_3
 2052 ?        00:00:00 scsi_eh_4
 2053 ?        00:00:00 scsi_eh_5
 2118 ?        00:00:00 knodemgrd_0
 2328 ?        02:22:05 kjournald
 2503 ?        00:00:01 udevd
 2658 ?        00:00:00 kmmcd
 3393 ?        00:00:00 skype
 3394 ?        00:14:45 skype.real
 3583 ?        00:00:00 kpsmoused
 3668 ?        00:00:57 simple-ccsm
 4210 ?        00:00:00 knotify
 4544 ?        00:00:12 kjournald
 4605 ?        00:00:04 gdm
 4608 tty9     16:30:19 Xorg
 4640 ?        00:00:00 gnome-keyring-d
 4650 ?        00:00:00 x-session-manag
 4700 ?        00:00:00 bluetoothd
 4708 ?        00:00:00 dbus-launch
 4709 ?        00:02:42 dbus-daemon
 4712 ?        02:04:52 pulseaudio
 4715 ?        00:00:00 gconf-helper
 4717 ?        00:01:39 gconfd-2
 4723 ?        00:00:00 seahorse-agent
 4726 ?        00:00:00 gvfsd
 4732 ?        00:01:43 gvfs-fuse-daemo
 4739 ?        00:00:00 gnome-keyring-d
 4741 ?        00:02:52 gnome-settings-
 4753 ?        00:03:56 gnome-panel
 4754 ?        00:00:54 nautilus
 4756 ?        00:00:00 bonobo-activati
 4761 ?        00:00:00 trackerd
 4765 ?        00:00:00 tracker-applet
 4767 ?        00:10:16 avant-window-na
 4771 ?        00:01:18 nm-applet
 4777 ?        00:00:01 python
 4781 ?        00:00:00 evolution-alarm
 4785 ?        00:01:49 python
 4786 ?        00:00:27 update-notifier
 4787 ?        00:00:00 python
 4789 ?        05:48:36 python
 4792 ?        00:00:01 fusion-icon
 4799 ?        00:00:02 mixer_applet2
 4801 ?        00:00:02 fast-user-switc
 4803 ?        00:00:00 bluetooth-apple
 4818 ?        00:00:50 gnome-power-man
 4820 tty4     00:00:00 getty
 4821 tty5     00:00:00 getty
 4828 tty2     00:00:00 getty
 4829 tty3     00:00:00 getty
 4830 tty6     00:00:00 getty
 4860 ?        00:00:03 gvfs-hal-volume
 4875 ?        00:00:00 evolution-data-
 4876 ?        00:05:04 gnome-screensav
 4889 ?        00:00:03 gvfs-gphoto2-vo
 4896 ?        00:00:00 gvfsd-burn
 4917 ?        04:02:53 compiz
 4934 ?        00:01:35 hald
 4935 ?        00:00:03 hald-runner
 4956 ?        00:00:00 evolution-excha
 4960 ?        00:00:01 hald-addon-inpu
 4975 ?        00:00:00 hald-addon-cpuf
 4976 ?        00:00:00 hald-addon-acpi
 4982 ?        00:00:00 gvfsd-trash
 4992 ?        00:04:26 hald-addon-stor
 5001 ?        00:00:00 sh
 5002 ?        00:04:55 emerald
 5005 ?        00:00:00 acpid
 5018 ?        00:00:00 awn-applet-acti
 5037 ?        00:00:41 kondemand/0
 5038 ?        00:00:00 kondemand/1
 5122 ?        00:00:03 syslogd
 5173 ?        00:00:00 dd
 5175 ?        00:00:00 klogd
 5198 ?        00:02:23 dbus-daemon
 5220 ?        00:00:01 avahi-daemon
 5221 ?        00:00:00 avahi-daemon
 5280 ?        00:00:00 mysqld_safe
 5322 ?        00:48:57 mysqld
 5324 ?        00:00:00 logger
 5431 ?        00:00:15 postgres
 5434 ?        00:02:06 postgres
 5435 ?        00:01:16 postgres
 5436 ?        00:00:20 postgres
 5437 ?        00:00:18 postgres
 5481 ?        00:00:11 cupsd
 5700 ?        00:18:14 ntos_wq
 5702 ?        00:00:00 ndis_wq
 5705 ?        00:00:26 wrapndis_wq
 5732 ?        00:00:00 dhclient
 5754 ?        00:00:38 notification-da
 5795 ?        00:00:43 dhcdbd
 5820 ?        00:00:35 console-kit-dae
 5942 ?        00:00:36 ntpd
 5978 ?        02:59:57 mythbackend
 6006 ?        00:00:00 btaddconn
 6007 ?        00:00:00 btdelconn
 6020 ?        00:00:00 krfcommd
 6067 ?        00:01:46 NetworkManager
 6077 ?        00:00:17 wpa_supplicant
 6079 ?        00:00:00 nm-system-setti
 6103 ?        00:00:00 gdm
 6130 ?        00:00:00 system-tools-ba
 6166 ?        00:00:00 atd
 6194 ?        00:00:02 cron
 6249 tty1     00:00:00 getty
 7926 ?        00:47:42 amarokapp
 7941 ?        00:00:00 kdeinit
 7944 ?        00:04:19 dcopserver
 7947 ?        00:00:43 klauncher
 7949 ?        00:00:58 kded
 7995 ?        00:00:00 kio_file
 7997 ?        00:00:00 ruby
 7998 ?        00:07:13 python
 8952 ?        00:00:00 autotorrent.rb
 9722 ?        00:00:25 npviewer.bin
14926 ?        00:00:00 gnome-terminal
14964 ?        00:00:00 gnome-pty-helpe
14965 pts/0    00:00:00 bash
15016 pts/0    00:00:00 ps
23726 ?        00:00:00 pdflush
23740 ?        00:00:16 pdflush
23983 ?        00:00:00 gvfsd-computer
25612 ?        00:00:00 sh
25613 ?        00:00:00 run-parts
25624 ?        00:00:00 apt
29022 ?        00:01:58 mount.ntfs-3g
29199 ?        00:01:24 apt-get
29202 ?        00:00:00 http
29206 ?        00:00:00 http
29207 ?        00:00:00 http
29208 ?        00:00:00 http
29209 ?        00:00:00 http
29211 ?        00:00:00 gpgv
29228 ?        00:00:00 bzip2
30463 ?        00:21:13 firefox

```

---

### Post by iamjfarrell on 2008-11-04
double post

---

### Post by taurus on 2008-11-04
> **iamjfarrell said:**
> ```

PID TTY          TIME CMD

25612 ?        00:00:00 sh
25613 ?        00:00:00 run-parts
**[COLOR="Blue"]25624 ?        00:00:00 apt[/COLOR]**
29022 ?        00:01:58 mount.ntfs-3g
**[COLOR="Blue"]29199 ?        00:01:24 apt-get[/COLOR]**
29202 ?        00:00:00 http
29206 ?        00:00:00 http
29207 ?        00:00:00 http
29208 ?        00:00:00 http
29209 ?        00:00:00 http
29211 ?        00:00:00 gpgv
29228 ?        00:00:00 bzip2
30463 ?        00:21:13 firefox

```

There you are.  So, you can either way for apt/apt-get finish doing what is doing in the background and run your apt-get once it's done.  Shouldn't be more than a few minutes.

---

### Post by iamjfarrell on 2008-11-04
> **taurus said:**
> There you are.  So, you can either way for apt/apt-get finish doing what is doing in the background and run your apt-get once it's done.  Shouldn't be more than a few minutes.

it has been doing whatever it is doing for a few days now. I don't know what it could be doing.

---

### Post by taurus on 2008-11-04
You can kill them both if you wish.

```
sudo kill -9 25624 29199
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jimv on 2008-11-04
A reboot should fix it.

Or run those commands the previous poster mentioned.

---

### Post by iamjfarrell on 2008-11-04
Genius! Thanks a lot!

---

