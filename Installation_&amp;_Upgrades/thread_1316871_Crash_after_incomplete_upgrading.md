---
title: "Crash after incomplete upgrading"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by argnur on 2009-11-06
Yesterday tried to upgrade my ubuntu Jaunty to Karmic (9.04 -> 9.10), but accidentally logged off (at some time in the beginning ). After that couldn't get into ubuntu any more, even via recovery mode. Tried to restore through live cd: mounted the partition, chroot'ed it and tried running these commands:[FONT=monospace]

[/FONT]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a
updating works but upgrading generates the following message with error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  dbus: Depends: upstart-job but it is not installable
        Depends: upstart (>= 0.6.3-6) but 0.3.9-8 is installed
  dmsetup: Depends: util-linux (>= 2.15-1) but 2.14.2-1ubuntu4 is installed
  gdm: Depends: upstart-job but it is not installable
  hal: Depends: upstart-job but it is not installable
  ifupdown: Depends: upstart (>= 0.6.0) but 0.3.9-8 is installed
  initramfs-tools: Depends: util-linux (> 2.15~rc1) but 2.14.2-1ubuntu4 is installed
  libc6-i686: PreDepends: libc6 (= 2.9-4ubuntu6.1) but 2.10.1-0ubuntu15 is installed
  libqt4-core: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
               Depends: libqt4-network (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
               Depends: libqt4-xml (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
               Depends: libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-designer: Depends: libqt4-xml (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                   Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                   Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-gui: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
              Depends: libqt4-opengl (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
              Depends: libqt4-assistant (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-help: Depends: libqt4-network (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
               Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
               Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-qt3support: Depends: libqt4-network (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                     Depends: libqt4-xml (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                     Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                     Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-script: Depends: libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                 Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-sql: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-sql-mysql: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-sql-sqlite: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-svg: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
              Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-test: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libqt4-xmlpatterns: Depends: libqt4-network (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                      Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  libxext-dev: Depends: libxext6 (= 2:1.0.99.1-0ubuntu4) but 2:1.0.99.1-0ubuntu3 is installed
  module-init-tools: Depends: upstart-job but it is not installable
  qt4-qtconfig: Depends: libqtcore4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
                Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but 4.5.0-0ubuntu4.2 is installed
  rsyslog: Depends: upstart-job but it is not installable
  udev: Depends: upstart-job but it is not installable
        Depends: util-linux (> 2.15~rc2) but 2.14.2-1ubuntu4 is installed
  usplash: Depends: upstart (>= 0.6.3-4) but 0.3.9-8 is installed
E: Unmet dependencies. Try using -f.
```installing generates:
```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libconvert-binhex-perl libsoap-lite-perl guile-1.8 latex2html libqt4-assistant libntfs10 x11proto-xext-dev lilypond-doc
  lilypond-data dia-libs libatk1.0-dev debhelper intltool-debian libuser-perl libglib2.0-dev texlive libmime-types-perl libcrypt-ssleay-perl
  libnet-ssleay-perl nvidia-settings x11proto-xinerama-dev gdesklets-data x11proto-render-dev dblatex mysql-gui-tools-common libsearchclient0
  libxrender-dev po-debconf libpt2.6.1-plugins-alsa python-qt4-common libsysfs-dev libdirectfb-extra libdebian-installer4 libossp-uuid-perl libpng12-dev
  libmime-tools-perl ubiquity-casper libxfce4util4 libfontconfig1-dev dnsmasq-base libmail-sendmail-perl libossp-uuid15 x11proto-composite-dev libecryptfs0
  rdate libopal3.6.1 libexo-0.3-0 libxcursor-dev libxfce4menu-0.1-0 libqt4-webkit mysql-admin asymptote python-soappy x11proto-randr-dev python-sip4
  x11proto-damage-dev libio-stringy-perl libtaglib2.0-cil libxcb-render-util0-dev libjpeg62-dev libnet-google-perl kbibtex libemail-date-format-perl
  libxdamage-dev nullmailer zlib1g-dev hddtemp libfreetype6-dev x11proto-fixes-dev netpbm lilypond libwww-search-perl os-prober thunar-data asymptote-doc
  libzip1 libmime-lite-perl imagemagick-doc libpt2.6.1 libudev0 libstrigihtmlgui0 ecryptfs-utils libfcgi-perl ubiquity-ubuntu-artwork libavahi1.0-cil
  libexpat1-dev python-fpconst dia-common libsigsegv0 libdebconfclient0 libnetpbm10 libgdict-1.0-6 html2text imagemagick libpixman-1-dev libxft-dev
  libjcode-pm-perl libio-socket-ssl-perl libpt2.6.1-plugins-v4l2 odt2txt libxcb-render0-dev libgmime2.2a-cil libxfixes-dev perl-doc libgsf0.0-cil keyutils
  libsys-hostname-long-perl libthunar-vfs-1-2 mono-gmcs nvidia-180-libvdpau libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support acpid alsa-base alsa-utils apmd apparmor apparmor-utils apport-qt avahi-daemon avahi-utils avant-window-navigator awn-applets-c-core
  awn-applets-python-core awn-manager beagle bluetooth bluez bluez-utils brltty brltty-x11 checkbox checkbox-gtk compiz compiz-gnome console-setup
  consolekit contact-lookup-applet dbus dbus-x11 deskbar-applet dia-gnome dkms dmsetup dolphin ekiga evolution evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal f-spot firefox-3.0-gnome-support firefox-gnome-support fuse-utils gdesklets gdm gdm-guest-session
  gnome-about gnome-applets gnome-control-center gnome-media gnome-mount gnome-netstatus-applet gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-spell gnome-user-guide gnome-user-guide-de gnome-user-guide-en
  gnome-user-guide-ru gnome-utils gparted grub gstreamer0.10-gnomevfs gvfs-fuse hal hal-cups-utils hotkey-setup hwtest hwtest-gtk ifupdown indicator-applet
  indicator-messages initramfs-tools jockey-common jockey-gtk kbd kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-bin-kde4 kdelibs-bin kdelibs5
  kfind khelpcenter4 kile konqueror konqueror-nsplugins konsole libawn-extras0 libawn0 libbonoboui2-0 libc6-i686 libcairo2-dev libdeskbar-tracker
  libdirectfb-dev libgail-gnome-module libgnome-media0 libgnome-pilot2 libgnome-vfs2.24-cil libgnome2-0 libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil
  libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-extra libgtk2.0-dev libgtkhtml-editor0 libgtkhtml3.14-19 libgtkhtml3.8-15
  libkonq5 liblpint-bonobo0 libnss-mdns libokularcore1 libpanel-applet2-0 libpango1.0-dev libqt4-core libqt4-designer libqt4-gui libqt4-help
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xmlpatterns libxcomposite-dev libxext-dev
  libxfcegui4-4 libxfconf-0-2 libxi-dev libxinerama-dev libxrandr-dev linux-generic linux-image-2.6.27-14-generic linux-image-2.6.28-11-generic
  linux-image-2.6.28-13-generic linux-image-2.6.28-14-generic linux-image-2.6.28-15-generic linux-image-2.6.28-16-generic linux-image-generic
  linux-restricted-modules-2.6.27-14-generic linux-restricted-modules-2.6.28-11-generic linux-restricted-modules-2.6.28-13-generic
  linux-restricted-modules-2.6.28-14-generic linux-restricted-modules-2.6.28-15-generic linux-restricted-modules-2.6.28-16-generic
  linux-restricted-modules-generic linux-sound-base module-init-tools mousetweaks mysql-query-browser nautilus nautilus-share network-manager
  network-manager-gnome ntfs-3g ntfsprogs nvidia-180-kernel-source nvidia-glx-180 okular pcmciautils pm-utils policykit policykit-1 policykit-1-gnome
  policykit-gnome powermgmt-base pulseaudio-module-hal python-awn python-awn-extras python-awnlib python-gnome2 python-gnome2-desktop python-pyatspi
  python-qt4 qt4-qtconfig rhythmbox rsyslog screem screenlets seahorse-plugins strigi-client strigi-daemon system-config-printer-gnome tomboy totem
  totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils tsclient ubiquity ubiquity-frontend-gtk ubuntu-docs ubuntu-minimal
  ubuntu-system-service udev update-notifier usplash usplash-theme-ubuntu vinagre vino wireless-crda xfce4-appfinder xfconf xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo xulrunner-1.9-gnome-support
  yelp
0 upgraded, 0 newly installed, 264 to remove and 2 not upgraded.
227 not fully installed or removed.
After this operation, 1130MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (1) on findutils

```tried also installing findutils: "**sudo aptitude install findutils**", but get "Processing was halted because there were too many errors." with many other lines like those generated by **sudo dpkg --configure -a**:

```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on upstart-job; however:
  Package upstart-job is not installed.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on util-linux (>> 2.15~rc1); however:
  Version of util-linux on system is 2.14.2-1ubuntu4.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of module-init-tools:
 module-init-tools depends on upstart-job; however:
  Package upstart-job is not installed.
dpkg: error processing module-init-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-gui:
 libqt4-gui depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.2.
 libqt4-gui depends on libqt4-opengl (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-opengl on system is 4.5.0-0ubuntu4.2.
 libqt4-gui depends on libqt4-assistant (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-assistant on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql-sqlite:
 libqt4-sql-sqlite depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-sql-sqlite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxext-dev:
 libxext-dev depends on libxext6 (= 2:1.0.99.1-0ubuntu4); however:
  Version of libxext6 on system is 2:1.0.99.1-0ubuntu3.
dpkg: error processing libxext-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql:
 libqt4-sql depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-sql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
dpkg: error processing bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxrandr-dev:
 libxrandr-dev depends on libxext-dev; however:
  Package libxext-dev is not configured yet.
dpkg: error processing libxrandr-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ifupdown:
 ifupdown depends on upstart (>= 0.6.0); however:
  Version of upstart on system is 0.3.9-8.
dpkg: error processing ifupdown (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
 libqt4-svg depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus:
 dbus depends on upstart-job; however:
  Package upstart-job is not installed.
 dbus depends on upstart (>= 0.6.3-6); however:
  Version of upstart on system is 0.3.9-8.
dpkg: error processing dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxi-dev:
 libxi-dev depends on libxext-dev; however:
  Package libxext-dev is not configured yet.
dpkg: error processing libxi-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal:
 hal depends on upstart-job; however:
  Package upstart-job is not installed.
 hal depends on dbus (>= 1.2.16-0ubuntu3); however:
  Package dbus is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on initramfs-tools (>= 0.85eubuntu12); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql-mysql:
 libqt4-sql-mysql depends on libqt4-sql (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-sql is not configured yet.
 libqt4-sql-mysql depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-sql-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:
 libqt4-script depends on libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-dbus on system is 4.5.0-0ubuntu4.2.
 libqt4-script depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-script (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing consolekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libxext-dev (>= 1:1.0.1-2); however:
  Package libxext-dev is not configured yet.
 libgtk2.0-dev depends on libxi-dev (>= 1:1.0.1-4); however:
  Package libxi-dev is not configured yet.
 libgtk2.0-dev depends on libxrandr-dev (>= 1:1.2.99); however:
  Package libxrandr-dev is not configured yet.
dpkg: error processing libgtk2.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqt4-script (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-script is not configured yet.
 libqt4-designer depends on libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-xml on system is 4.5.0-0ubuntu4.2.
 libqt4-designer depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
 libqt4-designer depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qt4-qtconfig:
 qt4-qtconfig depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
 qt4-qtconfig depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing qt4-qtconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-help:
 libqt4-help depends on libqt4-network (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-network on system is 4.5.0-0ubuntu4.2.
 libqt4-help depends on libqt4-sql (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-sql is not configured yet.
 libqt4-help depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
 libqt4-help depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-help (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brltty:
 brltty depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing brltty (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 dmsetup depends on util-linux (>= 2.15-1); however:
  Version of util-linux on system is 2.14.2-1ubuntu4.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
dpkg: error processing alsa-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdirectfb-dev:
 libdirectfb-dev depends on libxext-dev; however:
  Package libxext-dev is not configured yet.
dpkg: error processing libdirectfb-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-core:
 libqt4-core depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
 libqt4-core depends on libqt4-network (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-network on system is 4.5.0-0ubuntu4.2.
 libqt4-core depends on libqt4-script (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-script is not configured yet.
 libqt4-core depends on libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-xml on system is 4.5.0-0ubuntu4.2.
 libqt4-core depends on libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-dbus on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqt4-network (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-network on system is 4.5.0-0ubuntu4.2.
 libqt4-qt3support depends on libqt4-sql (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-sql is not configured yet.
 libqt4-qt3support depends on libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-xml on system is 4.5.0-0ubuntu4.2.
 libqt4-qt3support depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
 libqt4-qt3support depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-test:
 libqt4-test depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-test (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on upstart-job; however:
  Package upstart-job is not installed.
 udev depends on module-init-tools (>= 3.2.1-0ubuntu3); however:
  Package module-init-tools is not configured yet.
 udev depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
 udev depends on util-linux (>> 2.15~rc2); however:
  Version of util-linux on system is 2.14.2-1ubuntu4.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:
 libqt4-xmlpatterns depends on libqt4-network (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqt4-network on system is 4.5.0-0ubuntu4.2.
 libqt4-xmlpatterns depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.2.
dpkg: error processing libqt4-xmlpatterns (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
 ubuntu-minimal depends on ifupdown; however:
  Package ifupdown is not configured yet.
 ubuntu-minimal depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 ubuntu-minimal depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rsyslog:
 rsyslog depends on upstart-job; however:
  Package upstart-job is not installed.
dpkg: error processing rsyslog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on consolekit; however:
  Package consolekit is not configured yet.
 policykit-1 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usplash:
 usplash depends on initramfs-tools (>= 0.92bubuntu50); however:
  Package initramfs-tools is not configured yet.
 usplash depends on upstart (>= 0.6.3-4); however:
  Version of upstart on system is 0.3.9-8.
dpkg: error processing usplash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxcomposite-dev:
 libxcomposite-dev depends on libxext-dev; however:
  Package libxext-dev is not configured yet.
dpkg: error processing libxcomposite-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libdirectfb-dev (>= 0.9.25); however:
  Package libdirectfb-dev is not configured yet.
dpkg: error processing libcairo2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on libcairo2-dev (>= 1.8.2-2); however:
  Package libcairo2-dev is not configured yet.
dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on hal (>= 0.5.12~git20090406); however:
  Package hal is not configured yet.
 xserver-xorg depends on console-setup (>= 1.29) | console-setup-mini (>= 1.29); however:
  Package console-setup is not configured yet.
  Package console-setup-mini is not installed.
dpkg: error processing xserver-xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-1-gnome:
 policykit-1-gnome depends on policykit-1; however:
  Package policykit-1 is not configured yet.
dpkg: error processing policykit-1-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brltty-x11:
 brltty-x11 depends on brltty (= 4.0-7ubuntu2); however:
  Package brltty is not configured yet.
dpkg: error processing brltty-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on policykit-1-gnome; however:
  Package policykit-1-gnome is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on xserver-xorg; however:
  Package xserver-xorg is not configured yet.
dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.5.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-openchrome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.5.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.6.2); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-radeon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.6.2); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.5.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.6.2); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-rendition:
 xserver-xorg-video-rendition depends on xserver-xorg-core (>= 2:1.5.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-rendition (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 gdm
 initramfs-tools
 module-init-tools
 libqt4-gui
 libqt4-sql-sqlite
 libxext-dev
 libqt4-sql
 bluez
 libxrandr-dev
 ifupdown
 libqt4-svg
 dbus
 libxi-dev
 hal
 console-setup
 libqt4-sql-mysql
 libqt4-script
 consolekit
 libgtk2.0-dev
 libqt4-designer
 qt4-qtconfig
 libqt4-help
 brltty
 dmsetup
 alsa-utils
 libdirectfb-dev
 libqt4-core
 libqt4-qt3support
 libqt4-test
 udev
 libqt4-xmlpatterns
 ubuntu-minimal
 apparmor
 rsyslog
 policykit-1
 usplash
 libxcomposite-dev
 libcairo2-dev
 libpango1.0-dev
 xserver-xorg
 policykit-1-gnome
 brltty-x11
 gnome-session-bin
 xserver-xorg-core
 xserver-xorg-video-openchrome
 xserver-xorg-video-vmware
 xserver-xorg-video-radeon
 xserver-xorg-video-savage
 xserver-xorg-video-fbdev
 xserver-xorg-video-vesa
 xserver-xorg-video-rendition
Processing was halted because there were too many errors.

```Could anyone please help me? I would be eternally grateful :p.

---

### Post by jstalnak on 2009-11-06
Hmm -- you are where I was late yesterday afternoon and earlier this morning. I did as you've done:

1. Boot from LiveCD
2. Run terminal
3. #> sudo -i
4. #> mkdir /mnt/root
5. #> mount /dev/sda# /mnt/root
6. #> mount -o bind /dev /mnt/root/dev
7. #> mount -o bind /sys /mnt/root/sys
8. #> mount -o bind /proc /mnt/root/proc
9. #> chroot /mnt/root
10. #> dpkg --configure -a
11. #> etc.

All that you tried and I DID get the many endless pages of dependency errors and the eventual 'cancelled because too many errors'

But ... I then was able to boot to a recovery console using grub to the primary /root partition. From there, I edited /etc/apt/sources.list file to comment-out all items except the one for the ubuntu ALTERNATE cd for the karmic release.

I was then able to get to a root prompt via the main grub startup (i.e., not through loading a LiveCD session) and get the upgrade to complete without all of the dependency errors.

But ... I'm having significant issues getting my partitions to mount on boot -- one, an encrypted partition, is causing issues because the mountall phase of the init process won't let me type in the passphrase -- it keeps putting other text/warnings on the screen and it's interfering with my ability to actually enter the passphrase. GRRRR.

---

