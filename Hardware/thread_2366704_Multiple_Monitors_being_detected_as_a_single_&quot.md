---
title: "Multiple Monitors being detected as a single &quot;built-in&quot; display"
date: 2017-07-20
forum: Hardware
---

### Post by nolet-brandon on 2017-07-20
Hi all ):P,

I've pulled out my account just for this issue. Did a bunch of searching and it seems that nobody's posted about this issue before.

Ubuntu 16.04, fresh install, up-to-date as of posting, running the latest available kernel as of today.

Output of lspci command
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
03:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
05:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)

```

Output of ```
sudo systemctl status
```
```
&#9679; Coffee-Station
    State: running
     Jobs: 0 queued
   Failed: 0 units
    Since: Thu 2017-07-20 21:27:25 EDT; 19min ago
   CGroup: /
           &#9500;&#9472;init.scope
           &#9474; &#9492;&#9472;1 /sbin/init splash
           &#9500;&#9472;system.slice
           &#9474; &#9500;&#9472;avahi-daemon.service
           &#9474; &#9474; &#9500;&#9472;943 avahi-daemon: running [Coffee-Station.local
           &#9474; &#9474; &#9492;&#9472;991 avahi-daemon: chroot helpe
           &#9474; &#9500;&#9472;thermald.service
           &#9474; &#9474; &#9492;&#9472;904 /usr/sbin/thermald --no-daemon --dbus-enable
           &#9474; &#9500;&#9472;dbus.service
           &#9474; &#9474; &#9500;&#9472; 951 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
           &#9474; &#9474; &#9492;&#9472;1951 /usr/lib/x86_64-linux-gnu/fwupd/fwupd
           &#9474; &#9500;&#9472;ModemManager.service
           &#9474; &#9474; &#9492;&#9472;891 /usr/sbin/ModemManager
           &#9474; &#9500;&#9472;cron.service
           &#9474; &#9474; &#9492;&#9472;882 /usr/sbin/cron -f
           &#9474; &#9500;&#9472;wpa_supplicant.service
           &#9474; &#9474; &#9492;&#9472;1148 /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant
           &#9474; &#9500;&#9472;lightdm.service
           &#9474; &#9474; &#9500;&#9472;1091 /usr/sbin/lightdm
           &#9474; &#9474; &#9492;&#9472;1110 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
           &#9474; &#9500;&#9472;accounts-daemon.service
           &#9474; &#9474; &#9492;&#9472;884 /usr/lib/accountsservice/accounts-daemon
           &#9474; &#9500;&#9472;colord.service
           &#9474; &#9474; &#9492;&#9472;1333 /usr/lib/colord/colord
           &#9474; &#9500;&#9472;systemd-journald.service
           &#9474; &#9474; &#9492;&#9472;289 /lib/systemd/systemd-journald
           &#9474; &#9500;&#9472;snapd.service
           &#9474; &#9474; &#9492;&#9472;899 /usr/lib/snapd/snapd
           &#9474; &#9500;&#9472;udisks2.service
           &#9474; &#9474; &#9492;&#9472;1898 /usr/lib/udisks2/udisksd --no-debug
           &#9474; &#9500;&#9472;upower.service
           &#9474; &#9474; &#9492;&#9472;1292 /usr/lib/upower/upowerd
           &#9474; &#9500;&#9472;systemd-timesyncd.service
           &#9474; &#9474; &#9492;&#9472;847 /lib/systemd/systemd-timesyncd
           &#9474; &#9500;&#9472;systemd-logind.service
           &#9474; &#9474; &#9492;&#9472;921 /lib/systemd/systemd-logind
           &#9474; &#9500;&#9472;system-getty.slice
           &#9474; &#9474; &#9492;&#9472;getty@tty1.service
           &#9474; &#9474;   &#9492;&#9472;1127 /sbin/agetty --noclear tty1 linux
           &#9474; &#9500;&#9472;systemd-udevd.service
           &#9474; &#9474; &#9492;&#9472;317 /lib/systemd/systemd-udevd
           &#9474; &#9500;&#9472;polkitd.service
           &#9474; &#9474; &#9492;&#9472;1074 /usr/lib/policykit-1/polkitd --no-debug
           &#9474; &#9500;&#9472;cups-browsed.service
           &#9474; &#9474; &#9492;&#9472;1003 /usr/sbin/cups-browsed
           &#9474; &#9500;&#9472;NetworkManager.service
           &#9474; &#9474; &#9500;&#9472;1005 /usr/sbin/NetworkManager --no-daemon
           &#9474; &#9474; &#9500;&#9472;2106 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-wlp3s0.pid -lf /var/lib/NetworkManager/dhclient-453af70d-9780-41cb-9596-3b6d012a514d-wlp3s0.lease -cf /var/lib/NetworkManager/dhclient-wlp3s0.conf wlp3s0
           &#9474; &#9474; &#9492;&#9472;2120 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
           &#9474; &#9500;&#9472;irqbalance.service
           &#9474; &#9474; &#9492;&#9472;1076 /usr/sbin/irqbalance --pid=/var/run/irqbalance.pid
           &#9474; &#9500;&#9472;whoopsie.service
           &#9474; &#9474; &#9492;&#9472;913 /usr/bin/whoopsie -f
           &#9474; &#9500;&#9472;rsyslog.service
           &#9474; &#9474; &#9492;&#9472;925 /usr/sbin/rsyslogd -n
           &#9474; &#9500;&#9472;acpid.service
           &#9474; &#9474; &#9492;&#9472;896 /usr/sbin/acpid
           &#9474; &#9492;&#9472;rtkit-daemon.service
           &#9474;   &#9492;&#9472;1284 /usr/lib/rtkit/rtkit-daemon
           &#9492;&#9472;user.slice
             &#9492;&#9472;user-1000.slice
               &#9500;&#9472;user@1000.service
               &#9474; &#9492;&#9472;init.scope
               &#9474;   &#9500;&#9472;1392 /lib/systemd/systemd --user
               &#9474;   &#9492;&#9472;1400 (sd-pam)         
               &#9492;&#9472;session-c2.scope
                 &#9500;&#9472;1217 lightdm --session-child 12 19
                 &#9500;&#9472;1406 /usr/bin/gnome-keyring-daemon --daemonize --login
                 &#9500;&#9472;1415 /sbin/upstart --user
                 &#9500;&#9472;1498 upstart-udev-bridge --daemon --user
                 &#9500;&#9472;1506 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-zyRMPpSHog
                 &#9500;&#9472;1518 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
                 &#9500;&#9472;1547 upstart-file-bridge --daemon --user
                 &#9500;&#9472;1550 upstart-dbus-bridge --daemon --session --user --bus-name session
                 &#9500;&#9472;1554 upstart-dbus-bridge --daemon --system --user --bus-name system
                 &#9500;&#9472;1563 gpg-agent --homedir /home/brandon/.gnupg --use-standard-socket --daemon
                 &#9500;&#9472;1564 /usr/bin/ibus-daemon --daemonize --xim --address unix:tmpdir=/tmp/ibus
                 &#9500;&#9472;1579 /usr/lib/gvfs/gvfsd
                 &#9500;&#9472;1580 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
                 &#9500;&#9472;1585 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
                 &#9500;&#9472;1588 /usr/lib/ibus/ibus-dconf
                 &#9500;&#9472;1589 /usr/lib/ibus/ibus-ui-gtk3
                 &#9500;&#9472;1597 /usr/lib/ibus/ibus-x11 --kill-daemon
                 &#9500;&#9472;1612 /usr/lib/ibus/ibus-engine-simple
                 &#9500;&#9472;1624 /usr/lib/x86_64-linux-gnu/hud/hud-service
                 &#9500;&#9472;1626 /usr/lib/unity-settings-daemon/unity-settings-daemon
                 &#9500;&#9472;1631 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately
                 &#9500;&#9472;1633 /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
                 &#9500;&#9472;1640 /usr/lib/x86_64-linux-gnu/unity/unity-panel-service
                 &#9500;&#9472;1641 /usr/bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
                 &#9500;&#9472;1653 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
                 &#9500;&#9472;1676 /usr/lib/dconf/dconf-service
                 &#9500;&#9472;1690 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
                 &#9500;&#9472;1691 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
                 &#9500;&#9472;1692 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
                 &#9500;&#9472;1700 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
                 &#9500;&#9472;1704 /usr/lib/x86_64-linux-gnu/indicator-keyboard/indicator-keyboard-service --use-gtk
                 &#9500;&#9472;1705 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
                 &#9500;&#9472;1706 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
                 &#9500;&#9472;1707 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
                 &#9500;&#9472;1723 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
                 &#9500;&#9472;1752 /usr/bin/pulseaudio --start --log-target=syslog
                 &#9500;&#9472;1759 /usr/lib/evolution/evolution-source-registry
                 &#9500;&#9472;1774 compiz
                 &#9500;&#9472;1804 /usr/lib/evolution/evolution-calendar-factory
                 &#9500;&#9472;1811 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory contacts --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.Calendarx1804x2 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/Calendar/1804/2
                 &#9500;&#9472;1823 /usr/lib/evolution/evolution-addressbook-factory
                 &#9500;&#9472;1826 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory local --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.Calendarx1804x3 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/Calendar/1804/3
                 &#9500;&#9472;1838 /usr/lib/evolution/evolution-addressbook-factory-subprocess --factory local --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.AddressBookx1823x2 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/AddressBook/1823/2
                 &#9500;&#9472;1852 nautilus -n
                 &#9500;&#9472;1855 /usr/bin/gnome-software --gapplication-service
                 &#9500;&#9472;1859 nm-applet
                 &#9500;&#9472;1861 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
                 &#9500;&#9472;1864 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
                 &#9500;&#9472;1890 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
                 &#9500;&#9472;1922 /usr/lib/gvfs/gvfs-afc-volume-monitor
                 &#9500;&#9472;1928 /usr/lib/gvfs/gvfs-goa-volume-monitor
                 &#9500;&#9472;1933 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
                 &#9500;&#9472;1943 /usr/lib/gvfs/gvfs-mtp-volume-monitor
                 &#9500;&#9472;1966 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
                 &#9500;&#9472;1999 /usr/lib/firefox/firefox
                 &#9500;&#9472;2049 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
                 &#9500;&#9472;2094 /usr/lib/x86_64-linux-gnu/notify-osd
                 &#9500;&#9472;2261 zeitgeist-datahub
                 &#9500;&#9472;2268 /bin/sh -c /usr/lib/x86_64-linux-gnu/zeitgeist/zeitgeist-maybe-vacuum; /usr/bin/zeitgeist-daemon
                 &#9500;&#9472;2272 /usr/bin/zeitgeist-daemon
                 &#9500;&#9472;2279 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
                 &#9500;&#9472;2318 update-notifier
                 &#9500;&#9472;2345 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
                 &#9500;&#9472;2434 /usr/lib/firefox/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 1999 true plugin
                 &#9500;&#9472;2630 /usr/lib/gnome-terminal/gnome-terminal-server
                 &#9500;&#9472;2637 bash
                 &#9500;&#9472;2671 sudo systemctl status
                 &#9492;&#9472;2672 systemctl status


```

Contents of ```
/usr/share/X11/xorg.conf.d/10-amdgpu.conf
Section "OutputClass"
    Identifier "AMDgpu"
    MatchDriver "amdgpu"
    Driver "amdgpu"
EndSection

```

The CPU isn't a Xeon though, it's an i5-3570K

Lastly, both displays are functional and have the desktop being output to them. At the moment, I have a mirrored setup, but Screen Display in the settings shows single "Built-in Display" with no option to add a second one. 

If there's any other information that I can provide I'd be more than happy to. I just have no idea what this issue is related to and I'm thinking that my GPU my simply be gone caputz at this point. It's a few years old.

---

### Post by deadflowr on 2017-07-21
I think if you have it set to Mirrored, then it's only ever show you a single display, regardless of how many you attach.
I'm guessing you've toggle the mirror display settings on and off to see if it changes?
Other than that you can post your xrandr settings
```
xrandr -q
```
That at least will give us all a better feel of the situation at hand.

---

