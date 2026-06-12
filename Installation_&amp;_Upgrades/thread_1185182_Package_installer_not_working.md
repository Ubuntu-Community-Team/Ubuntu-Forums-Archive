---
title: "Package installer not working"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by BlackRat90 on 2009-06-12
I was trying to install amazon mp3 on my machine and when I ran the package installer it says it can't work because it can only run one software manger at a time? I checked the processes and it the only thing like that running...any one have an idea about what's wrong? or at least a alternative to installing amazon mp3? I'm running ubuntu 9.04 jaunty.

Thanks!
Rat~

---

### Post by Partyboi2 on 2009-06-12
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
ps -e
```

---

### Post by BlackRat90 on 2009-06-12
[FONT=arial][SIZE=2][COLOR=#000000]  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
    8 ?        00:00:00 kstop/0
    9 ?        00:00:00 kintegrityd/0
   10 ?        00:00:00 kblockd/0
   11 ?        00:00:00 kacpid
   12 ?        00:00:00 kacpi_notify
   13 ?        00:00:00 cqueue
   14 ?        00:00:01 ata/0
   15 ?        00:00:00 ata_aux
   16 ?        00:00:00 ksuspend_usbd
   17 ?        00:00:00 khubd
   18 ?        00:00:00 kseriod
   19 ?        00:00:00 kmmcd
   20 ?        00:00:00 btaddconn
   21 ?        00:00:00 btdelconn
   22 ?        00:00:00 pdflush
   23 ?        00:00:00 pdflush
   24 ?        00:00:00 kswapd0
   25 ?        00:00:00 aio/0
   26 ?        00:00:00 ecryptfs-kthrea
   29 ?        00:00:00 scsi_eh_0
   30 ?        00:00:00 scsi_eh_1
   31 ?        00:00:00 scsi_eh_2
   32 ?        00:00:00 scsi_eh_3
   33 ?        00:00:00 scsi_eh_4
   34 ?        00:00:00 scsi_eh_5
   35 ?        00:00:00 kstriped
   36 ?        00:00:00 kmpathd/0
   37 ?        00:00:00 kmpath_handlerd
   38 ?        00:00:00 ksnapd
   39 ?        00:00:00 kondemand/0
   40 ?        00:00:00 krfcommd
  765 ?        00:00:00 kjournald
  899 ?        00:00:00 udevd
 1487 ?        00:00:00 kpsmoused
 1633 ?        00:00:06 rtl8187
 2227 tty4     00:00:00 getty
 2228 tty5     00:00:00 getty
 2234 tty2     00:00:00 getty
 2236 tty3     00:00:00 getty
 2237 tty6     00:00:00 getty
 2307 ?        00:00:00 acpid
 2352 ?        00:00:00 syslogd
 2375 ?        00:00:00 dd
 2377 ?        00:00:00 klogd
 2400 ?        00:00:03 dbus-daemon
 2528 ?        00:00:00 winbindd
 2550 ?        00:00:02 hald
 2553 ?        00:00:00 winbindd
 2554 ?        00:00:01 console-kit-dae
 2617 ?        00:00:00 hald-runner
 2647 ?        00:00:01 hald-addon-inpu
 2693 ?        00:00:03 hald-addon-stor
 2694 ?        00:00:00 hald-addon-cpuf
 2695 ?        00:00:00 hald-addon-acpi
 2713 ?        00:00:00 bluetoothd
 2746 ?        00:00:00 gdm
 2749 ?        00:00:00 gdm
 2753 tty7     00:01:24 Xorg
 2773 ?        00:00:02 NetworkManager
 2778 ?        00:00:00 wpa_supplicant
 2781 ?        00:00:00 nm-system-setti
 2797 ?        00:00:00 avahi-daemon
 2798 ?        00:00:00 avahi-daemon
 2821 ?        00:00:00 cupsd
 2849 ?        00:00:00 system-tools-ba
 2923 ?        00:00:00 atd
 2954 ?        00:00:00 cron
 3048 tty1     00:00:00 getty
 3337 ?        00:00:00 gnome-keyring-d
 3350 ?        00:00:00 x-session-manag
 3404 ?        00:00:00 ssh-agent
 3407 ?        00:00:00 dbus-launch
 3408 ?        00:00:00 dbus-daemon
 3413 ?        00:00:10 pulseaudio
 3414 ?        00:00:00 gconf-helper
 3416 ?        00:00:03 gconfd-2
 3427 ?        00:00:00 seahorse-agent
 3432 ?        00:00:03 gnome-settings-
 3440 ?        00:00:00 gvfsd
 3442 ?        00:00:00 compiz
 3451 ?        00:00:00 gvfs-fuse-daemo
 3512 ?        00:00:25 compiz.real
 3513 ?        00:00:13 gnome-panel
 3514 ?        00:00:25 nautilus
 3516 ?        00:00:00 bonobo-activati
 3519 ?        00:00:00 bluetooth-apple
 3521 ?        00:00:01 update-notifier
 3525 ?        00:00:00 python
 3529 ?        00:00:00 evolution-alarm
 3532 ?        00:00:05 nm-applet
 3538 ?        00:00:00 gnome-power-man
 3540 ?        00:00:00 notify-osd
 3544 ?        00:00:00 trashapplet
 3547 ?        00:00:00 gvfs-hal-volume
 3549 ?        00:00:00 gvfs-gphoto2-vo
 3551 ?        00:00:04 gvfsd-trash
 3562 ?        00:00:00 fast-user-switc
 3565 ?        00:00:00 mixer_applet2
 3568 ?        00:00:00 indicator-apple
 3573 ?        00:00:00 sh
 3574 ?        00:00:00 compiz-decorato
 3576 ?        00:00:02 gtk-window-deco
 3581 ?        00:00:00 gvfsd-burn
 3605 ?        00:00:00 dhclient
 3667 ?        00:04:33 firefox
 3682 ?        00:00:06 gnome-screensav
 3686 ?        00:00:00 evolution-data-
 3690 ?        00:00:00 evolution-excha
 3712 ?        00:00:00 system-service-
21507 ?        00:00:00 gnome-terminal
21508 ?        00:00:00 gnome-pty-helpe
21509 pts/0    00:00:00 bash
21526 pts/0    00:00:00 ps


sorry for the late reply
[/COLOR][/SIZE][/FONT]

---

### Post by BlackRat90 on 2009-06-12
bump?

---

### Post by Partyboi2 on 2009-06-12
Open a terminal and change to where you have downloaded the amazonmp3.deb package
eg if its on the Desktop
```
cd ~/Desktop
```
then
```
sudo dpkg -i amazonmp3.deb
```

---

### Post by BlackRat90 on 2009-06-13
Selecting previously deselected package amazonmp3.
(Reading database ... 103308 files and directories currently installed.)
Unpacking amazonmp3 (from amazonmp3.deb) ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libboost-thread1.34.1; however:
  Package libboost-thread1.34.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1 is not installed.
 amazonmp3 depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 amazonmp3


i dont think it worked, i might have fixed the problem. im going to try the package installer one last time

---

### Post by BlackRat90 on 2009-06-13
There it fixed!! my add/remove software program was running because i had had problems installing eternal lands yesterday! reinstalled the game and now its working!! thanks for your help!!

---

