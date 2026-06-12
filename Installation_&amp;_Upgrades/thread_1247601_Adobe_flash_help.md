---
title: "Adobe flash help"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by psychobilly freakout on 2009-08-23
Im trying to install the flash player and it's not letting me, everytime it finishes downloading i click "install package"  and i get this message

"Only 1 software management tool is allowed to run at the same time"

How can a management tool be open if the only thing i am using right now is firefox?

---

### Post by Partyboi2 on 2009-08-23
hi, open a terminal and have a look at your running processes to check no package manager is running
```
ps -e
```
If there is you will need to kill the process.
```
sudo kill PID
```
* Change 'Pid" to actually proccess number.

---

### Post by psychobilly freakout on 2009-08-23
Hi,

Im  be getting the same error message.

---

### Post by Partyboi2 on 2009-08-23
When you ran the ps -e command was their any package managers listed as running?

---

### Post by psychobilly freakout on 2009-08-23
This is what i get 

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   12 ?        00:00:00 kstop/0
   13 ?        00:00:00 kstop/1
   14 ?        00:00:00 kintegrityd/0
   15 ?        00:00:00 kintegrityd/1
   16 ?        00:00:00 kblockd/0
   17 ?        00:00:00 kblockd/1
   18 ?        00:00:00 kacpid
   19 ?        00:00:00 kacpi_notify
   20 ?        00:00:00 cqueue
   21 ?        00:00:00 ata/0
   22 ?        00:00:00 ata/1
   23 ?        00:00:00 ata_aux
   24 ?        00:00:00 ksuspend_usbd
   25 ?        00:00:00 khubd
   26 ?        00:00:00 kseriod
   27 ?        00:00:00 kmmcd
   28 ?        00:00:00 btaddconn
   29 ?        00:00:00 btdelconn
   30 ?        00:00:00 pdflush
   32 ?        00:00:02 kswapd0
   33 ?        00:00:00 aio/0
   34 ?        00:00:00 aio/1
   35 ?        00:00:00 ecryptfs-kthrea
   38 ?        00:00:00 scsi_eh_0
   39 ?        00:00:01 scsi_eh_1
   40 ?        00:00:00 kstriped
   41 ?        00:00:00 kmpathd/0
   42 ?        00:00:00 kmpathd/1
   43 ?        00:00:00 kmpath_handlerd
   44 ?        00:00:00 ksnapd
   45 ?        00:00:00 kondemand/0
   46 ?        00:00:00 kondemand/1
   47 ?        00:00:00 krfcommd
  295 ?        00:00:00 khpsbpkt
  311 ?        00:00:00 knodemgrd_0
  722 ?        00:00:51 mount.ntfs
  729 ?        00:00:06 loop0
  738 ?        00:00:00 kjournald
  873 ?        00:00:00 udevd
 1469 ?        00:00:00 pdflush
 1523 ?        00:00:00 pccardd
 1534 ?        00:00:00 kpsmoused
 1596 ?        00:01:24 ath5k_pci
 2772 tty4     00:00:00 getty
 2773 tty5     00:00:00 getty
 2780 tty2     00:00:00 getty
 2781 tty3     00:00:00 getty
 2782 tty6     00:00:00 getty
 2847 ?        00:00:00 acpid
 2922 ?        00:00:00 syslogd
 2945 ?        00:00:00 dd
 2947 ?        00:00:00 klogd
 2970 ?        00:00:05 dbus-daemon
 3027 ?        00:00:03 hald
 3030 ?        00:00:00 console-kit-dae
 3093 ?        00:00:00 hald-runner
 3123 ?        00:00:00 hald-addon-inpu
 3172 ?        00:00:02 hald-addon-stor
 3179 ?        00:00:00 hald-addon-cpuf
 3180 ?        00:00:00 hald-addon-acpi
 3192 ?        00:00:00 bluetoothd
 3225 ?        00:00:00 gdm
 3228 ?        00:00:00 gdm
 3232 tty7     00:04:13 Xorg
 3256 ?        00:00:03 NetworkManager
 3268 ?        00:00:00 wpa_supplicant
 3269 ?        00:00:00 nm-system-setti
 3280 ?        00:00:00 avahi-daemon
 3281 ?        00:00:00 avahi-daemon
 3310 ?        00:00:00 cupsd
 3338 ?        00:00:00 system-tools-ba
 3411 ?        00:00:00 atd
 3439 ?        00:00:00 cron
 3538 tty1     00:00:00 getty
 3561 ?        00:00:00 gnome-keyring-d
 3574 ?        00:00:00 x-session-manag
 3733 ?        00:00:00 ssh-agent
 3736 ?        00:00:00 dbus-launch
 3737 ?        00:00:04 dbus-daemon
 3742 ?        00:00:00 pulseaudio
 3743 ?        00:00:00 gconf-helper
 3745 ?        00:00:06 gconfd-2
 3757 ?        00:00:00 seahorse-agent
 3764 ?        00:00:05 gnome-settings-
 3770 ?        00:00:00 compiz
 3773 ?        00:00:00 gvfsd
 3806 ?        00:00:00 gvfs-fuse-daemo
 3846 ?        00:00:34 compiz.real
 3847 ?        00:00:20 gnome-panel
 3848 ?        00:00:02 nautilus
 3850 ?        00:00:00 bonobo-activati
 3854 ?        00:00:03 python
 3856 ?        00:00:00 bluetooth-apple
 3859 ?        00:00:01 update-notifier
 3865 ?        00:00:01 trackerd
 3868 ?        00:00:05 nm-applet
 3870 ?        00:00:00 evolution-alarm
 3871 ?        00:00:00 tracker-applet
 3876 ?        00:00:01 gnome-power-man
 3879 ?        00:00:00 notify-osd
 3893 ?        00:00:00 gvfsd-trash
 3941 ?        00:00:00 trashapplet
 3943 ?        00:00:00 gvfs-hal-volume
 3945 ?        00:00:00 gvfs-gphoto2-vo
 3946 ?        00:00:00 sh
 3947 ?        00:00:00 compiz-decorato
 3949 ?        00:00:12 gtk-window-deco
 3952 ?        00:00:02 fast-user-switc
 3956 ?        00:00:00 mixer_applet2
 3959 ?        00:00:00 gvfsd-burn
 3963 ?        00:00:00 tracker-indexer
 3980 ?        00:00:00 dhclient
 3986 ?        00:00:14 gnome-screensav
 4091 ?        00:00:01 indicator-apple
 4498 ?        00:06:01 firefox
 4512 ?        00:00:05 gksu
 4516 ?        00:00:07 gdebi-gtk
 5494 ?        00:00:40 pidgin
16129 ?        00:00:00 gvfsd-http
16135 ?        00:00:00 gnome-terminal
16136 ?        00:00:00 gnome-pty-helpe
16137 pts/0    00:00:00 bash
16154 pts/0    00:00:00 ps

---

### Post by Partyboi2 on 2009-08-23
Since there does not appear to be any package managers running, open a terminal and remove the lock file
```
sudo rm /var/lib/dpkg/lock
```
then try installing adobe flash again.

---

