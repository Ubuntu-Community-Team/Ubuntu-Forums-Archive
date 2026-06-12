---
title: "DualHeads+4Monitors not work in Xinerama/TwinView/separate properly 14.04.01"
date: 2014-09-27
forum: Hardware
---

### Post by oblus2 on 2014-09-27
Hi
From a week Im trying to enable all 4 monitors on 2 graphic cards with no luck...
What I want is to heve all screens on Right.
I'll paste few infos here:

my distro is Ubuntu GNOME 14.04.1 LTS

uname -a
```

Linux szuflandia 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux

```

xrandr -q
```

Screen 0: minimum 8 x 8, current 2648 x 1024, maximum 4096 x 4096
Unknown-0 connected primary 1368x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1368x768       60.0*+
   1280x720       60.0
   1152x720       60.0
   1024x768       60.0
   1024x576       60.0
   800x600        60.3
   640x480        59.9
Unknown-1 connected 1280x1024+1368+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   800x600        75.0     72.2     60.3     56.2
   640x480        75.0     72.8     59.9
Unknown-2 disconnected (normal left inverted right x axis y axis)
Unknown-3 disconnected (normal left inverted right x axis y axis)

```

xrandr --screen 1

```

Screen 1: minimum 8 x 8, current 2560 x 1024, maximum 8192 x 8192
DVI-I-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0*+
   1280x960       60.0
   1024x768       75.0     70.1     60.0
   800x600        75.0     72.2     60.3     56.2
   640x480        75.0     72.8     60.0     59.9
DVI-I-1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0*+
   1280x960       60.0
   1024x768       75.0     70.1     60.0
   800x600        75.0     72.2     60.3     56.2
   640x480        75.0     72.8     60.0     59.9
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)

```

nvidia-xconfig --query-gpu-info
```

Number of GPUs: 2

GPU #0:
  Name      : GeForce 6200
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-0):
      EDID Name             : BenQ G922HDL
      Minimum HorizSync     : 24.000 kHz
      Maximum HorizSync     : 63.000 kHz
      Minimum VertRefresh   : 50 Hz
      Maximum VertRefresh   : 76 Hz
      Maximum PixelClock    : 110.000 MHz
      Maximum Width         : 1366 pixels
      Maximum Height        : 768 pixels
      Preferred Width       : 1366 pixels
      Preferred Height      : 768 pixels
      Preferred VertRefresh : 60 Hz
      Physical Width        : 410 mm
      Physical Height       : 230 mm

  Display Device 1 (CRT-1):
      EDID Name             : Philips 190S5
      Minimum HorizSync     : 30.000 kHz
      Maximum HorizSync     : 82.000 kHz
      Minimum VertRefresh   : 56 Hz
      Maximum VertRefresh   : 76 Hz
      Maximum PixelClock    : 140.000 MHz
      Maximum Width         : 1280 pixels
      Maximum Height        : 1024 pixels
      Preferred Width       : 1280 pixels
      Preferred Height      : 1024 pixels
      Preferred VertRefresh : 60 Hz
      Physical Width        : 380 mm
      Physical Height       : 300 mm


GPU #1:
  Name      : Quadro NVS 290
  PCI BusID : PCI:4:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-0):
      EDID Name             : Mitac LCD Monitor
      Minimum HorizSync     : 31.000 kHz
      Maximum HorizSync     : 80.000 kHz
      Minimum VertRefresh   : 56 Hz
      Maximum VertRefresh   : 75 Hz
      Maximum PixelClock    : 135.000 MHz
      Maximum Width         : 1280 pixels
      Maximum Height        : 1024 pixels
      Physical Width        : 340 mm
      Physical Height       : 270 mm

  Display Device 1 (CRT-1):
      EDID Name             : Mitac LCD Monitor
      Minimum HorizSync     : 31.000 kHz
      Maximum HorizSync     : 80.000 kHz
      Minimum VertRefresh   : 56 Hz
      Maximum VertRefresh   : 75 Hz
      Maximum PixelClock    : 135.000 MHz
      Maximum Width         : 1280 pixels
      Maximum Height        : 1024 pixels
      Physical Width        : 340 mm
      Physical Height       : 270 mm

```

pstree -ach
```

[1minit[0m
  |-ModemManager
  |   |-{ModemManager}
  |   `-{ModemManager}
  |-NetworkManager
  |   |-dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf ...
  |   |-dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces--pid-file=/run/sendsigs.omit.d/network-manager.dnsm
  |   |-{NetworkManager}
  |   |-{NetworkManager}
  |   `-{NetworkManager}
  |-accounts-daemon
  |   |-{accounts-daemon}
  |   `-{accounts-daemon}
  |-acpid -c /etc/acpi/events -s /var/run/acpid.socket
  |-apache2 -k start
  |   |-apache2 -k start
  |   |-apache2 -k start
  |   |-apache2 -k start
  |   |-apache2 -k start
  |   `-apache2 -k start
  |-arpwatch -u arpwatch -N -p
  |-avahi-daemon
  |   `-avahi-daemon
  |-bandwidthd
  |   |-bandwidthd
  |   |   `-(bandwidthd)
  |   |-bandwidthd
  |   |   `-(bandwidthd)
  |   |-bandwidthd
  |   |   `-(bandwidthd)
  |   `-(bandwidthd)
  |-bluetoothd
  |-colord
  |   |-{colord}
  |   `-{colord}
  |-console-kit-dae --no-daemon
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   |-{console-kit-dae}
  |   `-{console-kit-dae}
  |-cron
  |-cups-browsed
  |-cupsd -f
  |-dbus-daemon --system --fork
  |-dbus-daemon --fork --print-pid 5 --print-address 7 --session
  |-dbus-launch --autolaunch=6b57fd0340115fc7563aab4d5418a85c --binary-syntax --close-stderr
  |-freshclam -d --quiet
  |-gdm
  |   |-gdm-simple-slav --display-id /org/gnome/DisplayManager/Displays/_0
  |   |   |-Xorg :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-h2W5y4/database -seat seat0 -nolisten tcp vt7
  |   |   |-gdm-session-wor
  |   |   |   |-init --user
  |   |   |   |   |-at-spi-bus-laun --launch-immediately
  |   |   |   |   |   |-dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
  |   |   |   |   |   |-{at-spi-bus-laun}
  |   |   |   |   |   |-{at-spi-bus-laun}
  |   |   |   |   |   `-{at-spi-bus-laun}
  |   |   |   |   |-at-spi2-registr --use-gnome-session
  |   |   |   |   |   `-{at-spi2-registr}
  |   |   |   |   |-dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-pkw5HkawAI
  |   |   |   |   |-dconf-service
  |   |   |   |   |   |-{dconf-*********
  |   |   |   |   |   `-{dconf-*********
  |   |   |   |   |-evolution-calen
  |   |   |   |   |   |-{evolution-calen}
  |   |   |   |   |   |-{evolution-calen}
  |   |   |   |   |   |-{evolution-calen}
  |   |   |   |   |   `-{evolution-calen}
  |   |   |   |   |-evolution-sourc
  |   |   |   |   |   |-{evolution-sourc}
  |   |   |   |   |   `-{evolution-sourc}
  |   |   |   |   |-gconfd-2
  |   |   |   |   |-gnome-keyring-d --start --components=secrets
  |   |   |   |   |   |-{gnome-keyring-d}
  |   |   |   |   |   |-{gnome-keyring-d}
  |   |   |   |   |   |-{gnome-keyring-d}
  |   |   |   |   |   |-{gnome-keyring-d}
  |   |   |   |   |   `-{gnome-keyring-d}
  |   |   |   |   |-gnome-session --session=gnome
  |   |   |   |   |   |-deja-dup-monito
  |   |   |   |   |   |   |-{deja-dup-monito}
  |   |   |   |   |   |   `-{deja-dup-monito}
  |   |   |   |   |   |-evolution-alarm
  |   |   |   |   |   |   |-{evolution-alarm}
  |   |   |   |   |   |   |-{evolution-alarm}
  |   |   |   |   |   |   |-{evolution-alarm}
  |   |   |   |   |   |   `-{evolution-alarm}
  |   |   |   |   |   |-gnome-shell --replace --display=:0
  |   |   |   |   |   |   |-{gnome-shell}
  |   |   |   |   |   |   |-{gnome-shell}
  |   |   |   |   |   |   |-{gnome-shell}
  |   |   |   |   |   |   |-{gnome-shell}
  |   |   |   |   |   |   |-{gnome-shell}
  |   |   |   |   |   |   `-{gnome-shell}
  |   |   |   |   |   |-nautilus -n
  |   |   |   |   |   |   |-{nautilus}
  |   |   |   |   |   |   |-{nautilus}
  |   |   |   |   |   |   `-{nautilus}
  |   |   |   |   |   |-psensor
  |   |   |   |   |   |   |-{psensor}
  |   |   |   |   |   |   `-{psensor}
  |   |   |   |   |   |-tracker-miner-f
  |   |   |   |   |   |   |-{tracker-miner-f}
  |   |   |   |   |   |   |-{tracker-miner-f}
  |   |   |   |   |   |   `-{tracker-miner-f}
  |   |   |   |   |   |-tracker-store
  |   |   |   |   |   |   |-{tracker-store}
  |   |   |   |   |   |   |-{tracker-store}
  |   |   |   |   |   |   |-{tracker-store}
  |   |   |   |   |   |   |-{tracker-store}
  |   |   |   |   |   |   |-{tracker-store}
  |   |   |   |   |   |   |-{tracker-store}
  |   |   |   |   |   |   `-{tracker-store}
  |   |   |   |   |   |-update-notifier
  |   |   |   |   |   |   |-{update-notifier}
  |   |   |   |   |   |   |-{update-notifier}
  |   |   |   |   |   |   `-{update-notifier}
  |   |   |   |   |   |-{gnome-session}
  |   |   |   |   |   |-{gnome-session}
  |   |   |   |   |   `-{gnome-session}
  |   |   |   |   |-gnome-settings-
  |   |   |   |   |   |-{gnome-settings-}
  |   |   |   |   |   |-{gnome-settings-}
  |   |   |   |   |   `-{gnome-settings-}
  |   |   |   |   |-gnome-shell-cal
  |   |   |   |   |   |-{gnome-shell-cal}
  |   |   |   |   |   |-{gnome-shell-cal}
  |   |   |   |   |   |-{gnome-shell-cal}
  |   |   |   |   |   `-{gnome-shell-cal}
  |   |   |   |   |-goa-daemon
  |   |   |   |   |   |-{goa-daemon}
  |   |   |   |   |   |-{goa-daemon}
  |   |   |   |   |   `-{goa-daemon}
  |   |   |   |   |-gsd-printer
  |   |   |   |   |   `-{gsd-printer}
  |   |   |   |   |-gvfs-afc-volume
  |   |   |   |   |   |-{gvfs-afc-volume}
  |   |   |   |   |   `-{gvfs-afc-volume}
  |   |   |   |   |-gvfs-goa-volume
  |   |   |   |   |   `-{gvfs-goa-volume}
  |   |   |   |   |-gvfs-gphoto2-vo
  |   |   |   |   |   `-{gvfs-gphoto2-vo}
  |   |   |   |   |-gvfs-mtp-volume
  |   |   |   |   |   `-{gvfs-mtp-volume}
  |   |   |   |   |-gvfs-udisks2-vo
  |   |   |   |   |   |-{gvfs-udisks2-vo}
  |   |   |   |   |   `-{gvfs-udisks2-vo}
  |   |   |   |   |-gvfsd
  |   |   |   |   |   `-{gvfsd}
  |   |   |   |   |-gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
  |   |   |   |   |   `-{gvfsd-burn}
  |   |   |   |   |-gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
  |   |   |   |   |   |-{gvfsd-fuse}
  |   |   |   |   |   |-{gvfsd-fuse}
  |   |   |   |   |   |-{gvfsd-fuse}
  |   |   |   |   |   `-{gvfsd-fuse}
  |   |   |   |   |-gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
  |   |   |   |   |   |-{gvfsd-trash}
  |   |   |   |   |   `-{gvfsd-trash}
  |   |   |   |   |-ibus-daemon --daemonize --xim
  |   |   |   |   |   |-ibus-dconf
  |   |   |   |   |   |   |-{ibus-dconf}
  |   |   |   |   |   |   |-{ibus-dconf}
  |   |   |   |   |   |   `-{ibus-dconf}
  |   |   |   |   |   |-ibus-engine-sim
  |   |   |   |   |   |   |-{ibus-engine-sim}
  |   |   |   |   |   |   `-{ibus-engine-sim}
  |   |   |   |   |   |-ibus-ui-gtk3
  |   |   |   |   |   |   |-{ibus-ui-gtk3}
  |   |   |   |   |   |   |-{ibus-ui-gtk3}
  |   |   |   |   |   |   `-{ibus-ui-gtk3}
  |   |   |   |   |   |-{ibus-daemon}
  |   |   |   |   |   `-{ibus-daemon}
  |   |   |   |   |-ibus-x11 --kill-daemon
  |   |   |   |   |   |-{ibus-x11}
  |   |   |   |   |   `-{ibus-x11}
  |   |   |   |   |-mission-control
  |   |   |   |   |   |-{mission-control}
  |   |   |   |   |   `-{mission-control}
  |   |   |   |   |-pulseaudio --start --log-target=syslog
  |   |   |   |   |   |-{pulseaudio}
  |   |   |   |   |   `-{pulseaudio}
  |   |   |   |   |-ssh-agent -s
  |   |   |   |   |-upstart-dbus-br --daemon --system --user --bus-name system
  |   |   |   |   |-upstart-dbus-br --daemon --session --user --bus-name session
  |   |   |   |   |-upstart-event-b
  |   |   |   |   |-upstart-file-br --daemon --user
  |   |   |   |   |-zeitgeist-daemo
  |   |   |   |   |   `-{zeitgeist-daemo}
  |   |   |   |   |-zeitgeist-datah
  |   |   |   |   |   |-{zeitgeist-datah}
  |   |   |   |   |   |-{zeitgeist-datah}
  |   |   |   |   |   |-{zeitgeist-datah}
  |   |   |   |   |   `-{zeitgeist-datah}
  |   |   |   |   `-zeitgeist-fts
  |   |   |   |       |-cat
  |   |   |   |       `-{zeitgeist-fts}
  |   |   |   |-{gdm-session-wor}
  |   |   |   `-{gdm-session-wor}
  |   |   |-{gdm-simple-slav}
  |   |   `-{gdm-simple-slav}
  |   |-{gdm}
  |   `-{gdm}
  |-getty -8 38400 tty4
  |-getty -8 38400 tty5
  |-getty -8 38400 tty2
  |-getty -8 38400 tty3
  |-getty -8 38400 tty6
  |-getty -8 38400 tty1
  |-kerneloops
  |-mysqld
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   |-{mysqld}
  |   `-{mysqld}
  |-nmbd -D
  |-ntpd -p /var/run/ntpd.pid -g -u 119:128
  |-pdns_recursor
  |   |-{pdns_recursor}
  |   `-{pdns_recursor}
  |-polkitd --no-debug
  |   |-{polkitd}
  |   `-{polkitd}
  |-portsentry -tcp
  |-portsentry -udp
  |-postgres -D /var/lib/postgresql/9.3/main -c config_file=/etc/postgresql/9.3/main/postgresql.conf
  |   |-postgres                                                                                           
  |   |-postgres                                                                                                 
  |   |-postgres                                                                                             
  |   |-postgres                                                                                    
  |   `-postgres                                                                                        
  |-proftpd              
  |   `-proftpd              
  |-rsyslogd
  |   |-{rsyslogd}
  |   |-{rsyslogd}
  |   `-{rsyslogd}
  |-rtkit-daemon
  |   |-{rtkit-daemon}
  |   `-{rtkit-daemon}
  |-sensord -f daemon
  |-smbd -F
  |   `-smbd -F
  |-snort -m 027 -D -d -l /var/log/snort -u snort -g snort -c /etc/snort/snort.conf -S HOME_NET=[10.0.0.0/8] -i eth0
  |   `-{snort}
  |-[1msshd[0m -D
  |   `-[1msshd[0m  
  |       `-[1msshd[0m   
  |           `-[1mbash[0m
  |               `-[1msu[0m -
  |                   `-[1mbash[0m
  |                       `-[1mscreen[0m
  |                           `-[1mscreen[0m
  |                               |-[1mbash[0m
  |                               |   `-[1mpstree[0m -ach
  |                               |-mc /var/log /home/oblus
  |                               |   `-bash -rcfile .bashrc
  |                               |-mc /etc/X11 /etc/X11
  |                               |   `-bash -rcfile .bashrc
  |                               `-mc /home/oblus /root
  |                                   `-bash -rcfile .bashrc
  |-systemd-logind
  |-systemd-udevd --daemon
  |-udisksd --no-debug
  |   |-{udisksd}
  |   |-{udisksd}
  |   |-{udisksd}
  |   `-{udisksd}
  |-upowerd
  |   |-{upowerd}
  |   `-{upowerd}
  |-upstart-file-br --daemon
  |-upstart-socket- --daemon
  |-upstart-udev-br --daemon
  |-whoopsie
  |   |-{whoopsie}
  |   `-{whoopsie}
  `-winbindd -F
      `-winbindd -F 

```

Now I'll attach some xorg configurations:
[ATTACH]256735[/ATTACH]
this configuration gives me deskto on first 2 display and on other two is only black screen and X cursor
I tried to workaround this by gnome-shell --replace --display=:0.1 and it worked but after that when I tried to run smth like gnome-settings or ony other program it fails:
[ATTACH]256736[/ATTACH]

[ATTACH]256737[/ATTACH]
with this configuration I want to enable Xinerama but with no luck - all black screens

[ATTACH]256738[/ATTACH]
this is similar configuration as above one

I've done both configurations based on google and users who have used them


Could someone can help me with this four monitors?

---

### Post by oblus2 on 2014-10-01
any one can help?!

---

### Post by didier5 on 2014-10-05
It seems you have NVIDIA graphical cards.

My advise - use drivers from NVIDIA - not default xorg.
Then create one X screen for each physical monitor.
Put recommended size and frequency for each screen.
So no primary screen?

Only at the end : xinerama.

---

