---
title: "Ubuntu 12.04 Update Breaks X.org ATi"
date: 2013-05-10
forum: Hardware
---

### Post by snafu006 on 2013-05-10
here spec first:

```
*-display               
       description: VGA compatible controller
       product: RS880M [Mobility Radeon HD 4200 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:e0000000-efffffff ioport:3000(size=256) memory:f0300000-f030ffff memory:f0200000-f02fffff

```

```
 uname -a
Linux snafu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Ok so there is a update that is breaking X.org. This is a re-re-reinstall because i cant find what update is doing this. This computer is a hp G62-340us AMD-ATi I have the 13.1 drivers installed and this old laptop can pay most of steam games so its nice to have working drivers.

But one of these updats are breaking x.org
```
The following packages will be upgraded:
  accountsservice acpi-support activity-log-manager-common
  activity-log-manager-control-center alsa-base alsa-utils apparmor
  appmenu-gtk appmenu-gtk3 apport apport-gtk apport-symptoms apt
  apt-transport-https apt-utils aptdaemon aptdaemon-data aptitude bamfdaemon
  base-files bash bind9-host brasero brasero-cdrkit brasero-common
  busybox-initramfs busybox-static checkbox checkbox-qt colord compiz
  compiz-core compiz-gnome compiz-plugins-default coreutils cups cups-bsd
  cups-client cups-common cups-ppdc dbus dbus-x11 deja-dup dmsetup
  dnsmasq-base dnsutils dpkg duplicity eog evince evince-common firefox
  firefox-globalmenu firefox-gnome-support firefox-locale-en fonts-opensymbol
  gdb geoclue-ubuntu-geoip ghostscript ghostscript-cups ghostscript-x
  gir1.2-dee-1.0 gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-webkit-3.0 glib-networking
  glib-networking-common glib-networking-services gnome-accessibility-themes
  gnome-control-center gnome-control-center-data gnome-games-data
  gnome-keyring gnome-media gnome-online-accounts gnome-power-manager
  gnome-screenshot gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv
  grub-common grub-pc grub-pc-bin grub2-common gstreamer0.10-gconf
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gvfs gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter im-switch indicator-messages
  indicator-status-provider-mc5 initramfs-tools initramfs-tools-bin iptables
  isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk
  landscape-client-ui-install language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector-common
  language-selector-gnome libaccountsservice0 libapt-inst1.4 libapt-pkg4.12
  libart-2.0-2 libasound2 libbamf0 libbamf3-0 libbind9-80 libbrasero-media3-1
  libc-bin libc-dev-bin libc6 libc6-dev libcolord1 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libcurl3-nss libdbus-1-3 libdbus-glib-1-2 libdecoration0
  libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1 libdns81
  libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libevince3-3
  libfreerdp-plugins-standard libfreerdp1 libfreetype6 libgail-3-0 libgck-1-0
  libgcr-3-1 libgcr-3-common libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglu1-mesa libgnome-control-center1 libgnome2-common libgnomekbd-common
  libgnomekbd7 libgnutls26 libgoa-1.0-0 libgoa-1.0-common libgs9 libgs9-common
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libgwibber-gtk2
  libgwibber2 libindicator-messages-status-provider1 libisc83 libisccc80
  libisccfg82 libjack-jackd2-0 libjavascriptcoregtk-3.0-0 libldap-2.4-2
  liblightdm-gobject-1-0 liblvm2app2.2 liblwres80 libnautilus-extension1a
  libneon27-gnutls libnih-dbus1 libnih1 libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnspr4 libnss3 libnux-2.0-0
  libnux-2.0-common liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0
  libpam-gnome-keyring libparted0debian1 libpciaccess0 libperl5.14
  libplymouth2 libpoppler-glib8 libpoppler19 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-style-tango
  libreoffice-writer librhythmbox-core5 libsmbclient libssh-4 libssl1.0.0
  libtelepathy-glib0 libtiff4 libtotem0 libudev0 libusbmuxd1 libwbclient0
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxcb-dri2-0
  libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1 libxml2
  libxrandr2 libxslt1.1 light-themes lightdm linux-firmware linux-libc-dev
  linux-sound-base login lsb-base lsb-release mahjongg make man-db mountall
  multiarch-support nautilus nautilus-data network-manager
  network-manager-gnome ntfs-3g nux-tools nvidia-common onboard openssh-client
  openssl overlay-scrollbar parted passwd perl perl-base perl-modules plymouth
  plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  policykit-1-gnome poppler-utils pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-gst0.10 python-keyring python-libproxy python-libxml2
  python-problem-report python-software-properties python-ubuntu-sso-client
  python-uno qdbus resolvconf rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rsyslog samba-common
  samba-common-bin seahorse sessioninstaller simple-scan smbclient
  software-center software-properties-common software-properties-gtk
  ssh-askpass-gnome sudo telepathy-idle thunderbird thunderbird-globalmenu
  thunderbird-gnome-support totem totem-common totem-mozilla totem-plugins
  transmission-common transmission-gtk tzdata ubuntu-desktop ubuntu-keyring
  ubuntu-minimal ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-standard udev
  unattended-upgrades unity-2d unity-greeter unity-lens-applications
  unity-scope-video-remote uno-libs3 update-manager update-manager-core
  update-notifier update-notifier-common upstart ure usbmuxd vino
  wpasupplicant x11-common x11-utils xdiagnose xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xterm xul-ext-ubufox
```

Is there a way to stop xserver updates, mesa and anyopen source drivers.

---

### Post by QIII on 2013-05-10
Hello!

When using the driver downloaded from ATI (as opposed to the driver in the repo), it is not uncommon for the driver to be broken by updates.

When I do updates, I watch specifically for any "linux-..." packages or anything to do with graphics.  If I find that, I answer "no" and stop the update.

I uninstall the driver using the amdconfig utility

```
sudo amdconfig --uninstall
```

Reboot.

Do the updates.

Reboot.

Reinstall the driver.

Reboot.

It's a bit of a pain, but I've generally found it to be effective.

Let me know if that helps.

Best wishes!

---

### Post by Werne on 2013-05-10
Yeah, well, ATI dropped support for 4000 series card (that would mean my own too) and each time Xorg or kernel gets updated, you need to reinstall fglrx. For that you have three possible solutions - don't use fglrx, reinstall fglrx after each update, or put the problematic updates on hold with aptitude.

Example of putting xserver-xorg package on hold with those:
```
aptitude hold xserver-xorg    #holds the update
aptitude unhold xserver-xorg    #now you can update it again
```

Those work fine for Debian 6/7, should work as well for Ubuntu provided that you have aptitude. If you don't, use
```
apt-get install aptitude
```
to get aptitude.

dpkg can also hold the update but I never used it, the commands for dpkg are:

```
echo "xserver-xorg hold" | dpkg --set selections    #holds the update
echo "xserver-xorg install" | dpkg --set-selections    #now you can update it again
```

Apt might be able to hold updates too but I can't say I use it much so I don't know.

---

### Post by snafu006 on 2013-05-10
> **QIII said:**
> Hello!

When using the driver downloaded from ATI (as opposed to the driver in the repo), it is not uncommon for the driver to be broken by updates.

When I do updates, I watch specifically for any "linux-..." packages or anything to do with graphics.  If I find that, I answer "no" and stop the update.

I uninstall the driver using the amdconfig utility

```
sudo amdconfig --uninstall
```

Reboot.

Do the updates.

Reboot.

Reinstall the driver.

Reboot.

It's a bit of a pain, but I've generally found it to be effective.

Let me know if that helps.

Best wishes!


OK that works thank you

---

