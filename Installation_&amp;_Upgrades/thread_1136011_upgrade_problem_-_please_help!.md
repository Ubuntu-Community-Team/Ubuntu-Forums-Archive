---
title: "upgrade problem - please help!"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Rex Regis on 2009-04-24
Ok, I have just installed ubuntu 8.10.  I am now trying to upgrade to 9.04 as it prompts me to do so on the update manager.  It all starts ok, then it tells me that third party sources have been disabled, and then gives this error:

> Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

Then follows a very long list of packages.

Having given the error, it closes and then informs me (on the taskbar) that I have 722 updates. when I go to the update manager again, they are not there, so I click check.  It goes through the motions, and then says:

> An error occurred

The following details are provided:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) intrepid Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures were invalid: NODATA 2


Having clicked close, it then just goes back to telling me that there is a disro upgrade to be installed.

I am quite new to linux, and don't really understand what is going on with this, and what these error messages mean.  Any help would be VERY much appreciated.

---

### Post by zvacet on 2009-04-24
In **system>admin>software sources<third party** uncheck all third party repos and then refresh.You can also try to switch from U.S. server to some other (main maybe).

---

### Post by Rex Regis on 2009-04-24
Thanks for your reply, but it didn't make any difference. The only difference is that now after the upgrade fails it tells me that there are 721 instead of 722 new updates.  If you have any more ideas is would be really helpful.

---

### Post by bngguy on 2009-04-24
> **Rex Regis said:**
> Thanks for your reply, but it didn't make any difference. The only difference is that now after the upgrade fails it tells me that there are 721 instead of 722 new updates.  If you have any more ideas is would be really helpful.

first find the best mirror server, this could be done by :

***System --> Administration --> Software Sources*** then select ***Other*** from the ***Download from:*** menu item.

then try to do the upgrade.

---

### Post by zvacet on 2009-04-24
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you get any errors post them here.

---

### Post by Rex Regis on 2009-04-24
> first find the best mirror server, this could be done by :

System --> Administration --> Software Sources then select Other from the Download from: menu item.

then try to do the upgrade.

I did this and it gave me this back:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  302 Moved Temporarily
Some index files failed to download, they have been ignored, or old ones used instead.

Then I did the second thing I was asked:


> Code:

sudo apt-get update && sudo apt-get dist-upgrade

If you get any errors post them here. 

This is the result:


```
Ign http://archive.ubuntu-rocks.org intrepid Release.gpg
Ign http://archive.ubuntu-rocks.org intrepid/main Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid/restricted Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid/universe Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid/multiverse Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates Release.gpg
Ign http://archive.ubuntu-rocks.org intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates/multiverse Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid Release        
Ign http://archive.ubuntu-rocks.org intrepid-updates Release
Ign http://archive.ubuntu-rocks.org intrepid/main Packages  
Ign http://archive.ubuntu-rocks.org intrepid/restricted Packages
Ign http://archive.ubuntu-rocks.org intrepid/main Sources
Ign http://archive.ubuntu-rocks.org intrepid/restricted Sources
Ign http://archive.ubuntu-rocks.org intrepid/universe Packages
Ign http://archive.ubuntu-rocks.org intrepid/universe Sources
Ign http://archive.ubuntu-rocks.org intrepid/multiverse Packages
Ign http://archive.ubuntu-rocks.org intrepid/multiverse Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/main Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/restricted Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/main Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/restricted Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/universe Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/universe Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/multiverse Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/multiverse Sources
Err http://archive.ubuntu-rocks.org intrepid/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/main Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/restricted Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/universe Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/universe Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/multiverse Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/multiverse Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/main Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/restricted Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/universe Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/universe Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/multiverse Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/multiverse Sources
  302 Moved Temporarily
W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  302 Moved Temporarily

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by bngguy on 2009-04-24
> **Rex Regis said:**
> I did this and it gave me this back:



Then I did the second thing I was asked:




This is the result:


```
Ign http://archive.ubuntu-rocks.org intrepid Release.gpg
Ign http://archive.ubuntu-rocks.org intrepid/main Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid/restricted Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid/universe Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid/multiverse Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates Release.gpg
Ign http://archive.ubuntu-rocks.org intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid-updates/multiverse Translation-en_US
Ign http://archive.ubuntu-rocks.org intrepid Release        
Ign http://archive.ubuntu-rocks.org intrepid-updates Release
Ign http://archive.ubuntu-rocks.org intrepid/main Packages  
Ign http://archive.ubuntu-rocks.org intrepid/restricted Packages
Ign http://archive.ubuntu-rocks.org intrepid/main Sources
Ign http://archive.ubuntu-rocks.org intrepid/restricted Sources
Ign http://archive.ubuntu-rocks.org intrepid/universe Packages
Ign http://archive.ubuntu-rocks.org intrepid/universe Sources
Ign http://archive.ubuntu-rocks.org intrepid/multiverse Packages
Ign http://archive.ubuntu-rocks.org intrepid/multiverse Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/main Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/restricted Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/main Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/restricted Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/universe Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/universe Sources
Ign http://archive.ubuntu-rocks.org intrepid-updates/multiverse Packages
Ign http://archive.ubuntu-rocks.org intrepid-updates/multiverse Sources
Err http://archive.ubuntu-rocks.org intrepid/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/main Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/restricted Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/universe Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/universe Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/multiverse Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid/multiverse Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/main Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/restricted Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/universe Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/universe Sources
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/multiverse Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org intrepid-updates/multiverse Sources
  302 Moved Temporarily
W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/multiverse/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/main/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  302 Moved Temporarily

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I think that mirror is down, go back to 

***System --> Administration --> Software Sources*** then select ***Other*** from the*** Download from:*** menu item.

In the mirrors list select ***mirrors.us.kernel.org***, there is a button on the right hand bottom corner " CHOOSE SERVER", then do the upgrade, i did mine from this mirror and it worked well.

---

### Post by Rex Regis on 2009-04-24
Thanks, but still no-go:

> Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

acpi
acpi-support
adduser
adobe-flashplugin
alacarte
alsa-base
alsa-utils
apmd
app-install-data
app-install-data-commercial
apparmor
apparmor-utils
apport
apport-gtk
apt
apt-transport-https
apt-utils
apt-xapian-index
aptitude
apturl
at
at-spi
avahi-autoipd
avahi-daemon
avahi-utils
avant-window-navigator
avant-window-navigator-data
awn-applets-c-core
awn-applets-c-extras
awn-applets-python-core
awn-applets-python-extras
awn-manager
base-files
base-passwd
bash
bash-completion
bind9-host
binutils
binutils-static
blt
bluetooth
bluez
bluez-alsa
bluez-cups
bluez-gnome
bluez-gstreamer
bluez-utils
brltty
brltty-x11
bsdmainutils
bsdutils
busybox-initramfs
bzip2
ca-certificates
capplets-data
cdparanoia
cdrdao
checkbox
checkbox-gtk
cli-common
command-not-found
command-not-found-data
compiz
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compiz-wrapper
compizconfig-backend-gconf
compizconfig-settings-manager
console-setup
console-terminus
consolekit
contact-lookup-applet
cpio
cpp
cpp-4.3
cron
cups
cups-bsd
cups-client
cups-common
cups-driver-gutenprint
cupsddk
cupsddk-drivers
dash
dbus
dbus-x11
dcraw
debconf
debconf-i18n
debianutils
deskbar-applet
desktop-file-utils
dhcp3-client
dhcp3-common
dictionaries-common
dmsetup
dnsmasq-base
dnsutils
doc-base
docbook-xml
dosfstools
dpkg
dvd+rw-tools
e2fslibs
e2fsprogs
ed
eject
ekiga
eog
esound-clients
esound-common
espeak
espeak-data
ethtool
evince
evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-documentation-en
evolution-exchange
evolution-plugins
evolution-webcal
example-content
f-spot
fast-user-switch-applet
fglrx-modaliases
file
file-roller
findutils
firefox
firefox-3.0
firefox-3.0-branding
firefox-3.0-gnome-support
firefox-gnome-support
fontconfig
fontconfig-config
foo2zjs
foomatic-db
foomatic-db-engine
foomatic-db-hpijs
foomatic-filters
fortune-mod
fortunes-min
freeglut3
friendly-recovery
fuse-utils
gamin
gcalctool
gcc
gcc-4.3
gcc-4.3-base
gconf-editor
gconf2
gconf2-common
gdebi
gdebi-core
gdm
gdm-guest-session
gedit
gedit-common
genisoimage
gettext-base
ghostscript
ghostscript-x
gimp
gimp-data
gksu
gnome-about
gnome-accessibility-themes
gnome-app-install
gnome-applets
gnome-applets-data
gnome-cards-data
gnome-control-center
gnome-desktop-data
gnome-doc-utils
gnome-games
gnome-games-data
gnome-icon-theme
gnome-keyring
gnome-mag
gnome-media
gnome-media-common
gnome-menus
gnome-mount
gnome-netstatus-applet
gnome-nettool
gnome-orca
gnome-panel
gnome-panel-data
gnome-pilot
gnome-power-manager
gnome-screensaver
gnome-session
gnome-settings-daemon
gnome-system-monitor
gnome-system-tools
gnome-terminal
gnome-terminal-data
gnome-themes
gnome-themes-selected
gnome-user-guide
gnome-user-guide-en
gnome-utils
grep
groff-base
grub
grub-common
gsfonts
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
gtk2-engines
gtk2-engines-murrine
gtk2-engines-pixbuf
gucharmap
guile-1.8-libs
gvfs
gvfs-backends
gvfs-bin
gvfs-fuse
hal
hal-cups-utils
hal-info
hdparm
hotkey-setup
hpijs
hplip
hplip-data
human-icon-theme
hwtest
hwtest-gtk
ifupdown
indicator-applet
indicator-messages
initramfs-tools
initscripts
iproute
iptables
iso-codes
jockey-common
jockey-gtk
kbd
klibc-utils
klogd
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
language-selector
language-selector-common
language-support-translations-en
laptop-detect
laptop-mode-tools
launchpad-integration
lftp
libao2
libapm1
libapparmor-perl
libapparmor1
libart2.24-cil
libasound2
libasound2-plugins
libass1
libatk1.0-0
libatk1.0-data
libatspi1.0-0
libattr1
libaudio2
libavahi-client3
libavahi-common-data
libavahi-common3
libavahi-compat-libdnssd1
libavahi-core5
libavahi-glib1
libavahi-gobject0
libavahi-ui0
libavcodec52
libavformat52
libavutil49
libawn-extras0
libawn0
libbeagle1
libbind9-40
libblkid1
libbluetooth3
libbonobo2-0
libbonobo2-common
libbonoboui2-0
libbonoboui2-common
libbrlapi0.5
libbz2-1.0
libc6
libc6-dev
libc6-i686
libcaca0
libcairo2
libcamel1.2-14
libcanberra-gtk-module
libcanberra-gtk0
libcanberra0
libcap2
libcdaudio1
libcdparanoia0
libcelt0
libck-connector0
libcolamd-3.2.0
libcomerr2
libcompizconfig0
libcompress-raw-zlib-perl
libcompress-zlib-perl
libcryptui0
libcucul0
libcups2
libcupsimage2
libcurl3
libcurl3-gnutls
libcwidget3
libdaemon0
libdb4.6
libdb4.7
libdbus-1-3
libdbus-glib-1-2
libdca0
libdecoration0
libdeskbar-tracker
libdevmapper1.02.1
libdirectfb-1.0-0
libdjvulibre-text
libdjvulibre21
libdns45
libdrm-intel1
libdrm2
libdvdnav4
libdvdread4
libebackend1.2-0
libebook1.2-9
libecal1.2-7
libedata-book1.2-2
libedata-cal1.2-6
libedataserver1.2-11
libedataserverui1.2-8
libeel2-2
libeel2-data
libegroupwise1.2-13
libenca0
libenchant1c2a
libept0
libesd-alsa0
libespeak1
libevdocument1
libevview1
libexchange-storage1.2-3
libexempi3
libffado0
libffi5
libflickrnet2.1.5-cil
libfontconfig1
libfreetype6
libfuse2
libgadu3
libgail-common
libgail-gnome-module
libgail18
libgamin0
libgc1c2
libgcc1
libgconf2-4
libgconf2.24-cil
libgcr0
libgcrypt11
libgdata-google1.2-1
libgdata1.2-1
libgdbm3
libgdict-1.0-6
libgdiplus
libgegl-0.0-0
libgif4
libgimp2.0
libgksu2-0
libgl1-mesa-dri
libgl1-mesa-glx
libglade2-0
libglade2.0-cil
libglib-perl
libglib2.0-0
libglib2.0-cil
libglib2.0-data
libglibmm-2.4-1c2a
libglu1-mesa
libgmime-2.0-2a
libgmime2.2a-cil
libgmp3c2
libgmyth0
libgnome-desktop-2-11
libgnome-keyring0
libgnome-keyring1.0-cil
libgnome-mag2
libgnome-media0
libgnome-menu2
libgnome-pilot2
libgnome-speech7
libgnome-vfs2.24-cil
libgnome-window-settings1
libgnome2-0
libgnome2-common
libgnome2.24-cil
libgnomecanvas2-0
libgnomecanvas2-common
libgnomecups1.0-1
libgnomekbd-common
libgnomekbd3
libgnomekbdui3
libgnomepanel2.24-cil
libgnomeprint2.2-0
libgnomeprint2.2-data
libgnomeprintui2.2-0
libgnomeprintui2.2-common
libgnomeui-0
libgnomeui-common
libgnomevfs2-0
libgnomevfs2-bin
libgnomevfs2-common
libgnomevfs2-extra
libgnutls26
libgomp1
libgp11-0
libgpgme11
libgphoto2-2
libgphoto2-port0
libgpm2
libgpod-common
libgpod4
libgraphviz4
libgs8
libgsf-1-114
libgsf-1-common
libgsl0ldbl
libgstreamer-plugins-base0.10-0
libgstreamer0.10-0
libgtk-vnc-1.0-0
libgtk2-perl
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-cil
libgtk2.0-common
libgtkhtml-editor-common
libgtkhtml-editor0
libgtkhtml3.14-19
libgtkmm-2.4-1c2a
libgtksourceview-common
libgtksourceview1.0-0
libgtksourceview2.0-0
libgtksourceview2.0-common
libgtkspell0
libgtop2-7
libgtop2-common
libgucharmap7
libgutenprint2
libgvfscommon0
libgweather-common
libgweather1
libhal-storage1
libhal1
libhesiod0
libhtml-parser-perl
libhunspell-1.2-0
libical0
libicu38
libidl0
libidn11
libieee1284-3
libijs-0.35
libilmbase6
libindicate1
libio-compress-base-perl
libio-compress-zlib-perl
libiptcdata0
libisc45
libisccc40
libisccfg40
libiw29
libjack0
libjasper1
libkeyutils1
libklibc
libkpathsea4
libkrb53
liblaunchpad-integration1
liblcms1
libldap-2.4-2
liblircclient0
liblockfile1
liblpint-bonobo0
liblrdf0
libltdl7
liblwres40
libmad0
libmagic1
libmagickcore1
libmagickwand1
libmailtools-perl
libmbca0
libmetacity0
libmodplug0c2
libmono-addins-gui0.2-cil
libmono-addins0.2-cil
libmono-cairo1.0-cil
libmono-cairo2.0-cil
libmono-corlib1.0-cil
libmono-corlib2.0-cil
libmono-data-tds1.0-cil
libmono-data-tds2.0-cil
libmono-data1.0-cil
libmono-data2.0-cil
libmono-getoptions1.0-cil
libmono-getoptions2.0-cil
libmono-i18n1.0-cil
libmono-i18n2.0-cil
libmono-posix1.0-cil
libmono-posix2.0-cil
libmono-security1.0-cil
libmono-security2.0-cil
libmono-sharpzip0.84-cil
libmono-sharpzip2.84-cil
libmono-sqlite2.0-cil
libmono-system-data1.0-cil
libmono-system-data2.0-cil
libmono-system-web1.0-cil
libmono-system-web2.0-cil
libmono-system1.0-cil
libmono-system2.0-cil
libmono0
libmono1.0-cil
libmono2.0-cil
libmpfr1ldbl
libmtp8
libmysqlclient15off
libnautilus-burn4
libnautilus-extension1
libncurses5
libncursesw5
libndesk-dbus-glib1.0-cil
libndesk-dbus1.0-cil
libneon27
libneon27-gnutls
libnewt0.52
libnm-glib0
libnm-util1
libnotify1
libnspr4-0d
libnss3-1d
libntfs-3g49
liboil0.3
liboobs-1-4
libopal3.6.1
libopenobex1
liborbit2
libpam-ck-connector
libpam-gnome-keyring
libpam-modules
libpam-runtime
libpam0g
libpanel-applet2-0
libpango1.0-0
libpango1.0-common
libpangomm-1.4-1
libparse-debianchangelog-perl
libparted1.8-10
libpcap0.8
libpci3
libpciaccess0
libpcre3
libpcsclite1
libperl5.10
libpisock9
libpisync1
libpixman-1-0
libpng12-0
libpolkit-dbus2
libpolkit-gnome0
libpolkit-grant2
libpolkit2
libpoppler-glib4
libpoppler4
libportaudio0
libportaudio2
libpostproc51
libpq5
libprotobuf3
libproxy0
libpt2.6.1
libpt2.6.1-plugins-alsa
libpt2.6.1-plugins-v4l2
libpth20
libpulse-browse0
libpulse0
libpulsecore9
libpurple-bin
libpurple0
libpython2.6
libraptor1
librasqal1
libraw1394-8
librdf0
libreadline5
librpc-xml-perl
librsvg2-2
librsvg2-common
libsamplerate0
libsane
libsasl2-2
libsasl2-modules
libscim8c2a
libsdl1.2debian
libsdl1.2debian-alsa
libselinux1
libsepol1
libshout3
libsilc-1.1-2
libslang2
libslp1
libsm6
libsmbclient
libsmbios2
libsndfile1
libsnmp-base
libsnmp15
libsoup-gnome2.4-1
libsoup2.4-1
libspectre1
libspeex1
libspeexdsp1
libsqlite3-0
libss2
libssl0.9.8
libstdc++6
libswscale0
libsysfs2
libtasn1-3
libtdb1
libterm-readkey-perl
libtheora0
libtidy-0.99-0
libtotem-plparser12
libtracker-gtk0
libtrackerclient0
libts-0.0-0
libtwolame0
libudev0
libunique-1.0-0
liburi-perl
libusb-0.1-4
libusplash0
libuuid-perl
libuuid1
libv4l-0
libvolume-id1
libvte-common
libvte9
libwavpack1
libwbclient0
libwebkit-1.0-1
libwmf0.2-7
libwnck-common
libwnck22
libwpg-0.1-1
libwrap0
libwv-1.2-3
libwww-perl
libx11-6
libx11-data
libx11-xcb1
libxau6
libxaw7
libxcb-render-util0
libxcb-render0
libxcb1
libxext6
libxft2
libxi6
libxkbfile1
libxklavier12
libxml++2.6-2
libxml-sax-expat-perl
libxml-twig-perl
libxml2
libxml2-utils
libxrandr2
libxslt1.1
libxt6
libxtst6
libxvmc1
libzephyr3
libzip1
linux-firmware
linux-generic
linux-headers-2.6.28-11
linux-headers-2.6.28-11-generic
linux-headers-generic
linux-image-2.6.28-11-generic
linux-image-generic
linux-libc-dev
linux-restricted-modules-2.6.28-11-generic
linux-restricted-modules-common
linux-restricted-modules-generic
linux-sound-base
locales
login
logrotate
lsb-base
lsb-release
lshw
ltrace
man-db
manpages
mawk
mbr
memtest86+
mesa-utils
metacity
metacity-common
min12xxw
mktemp
mlocate
mobile-broadband-provider-info
module-init-tools
mono-2.0-gac
mono-2.0-runtime
mono-common
mono-gac
mono-jit
mono-runtime
mount
mousetweaks
mtr-tiny
myspell-en-gb
myspell-en-za
mysql-common
nano
nautilus
nautilus-cd-burner
nautilus-data
nautilus-sendto
nautilus-share
ncurses-base
ncurses-bin
net-tools
netbase
network-manager
network-manager-gnome
notification-daemon
ntfs-3g
ntpdate
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-71-modaliases
nvidia-96-modaliases
nvidia-common
obex-data-server
odt2txt
openoffice.org-base-core
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-emailmerge
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-help-en-gb
openoffice.org-help-en-us
openoffice.org-impress
openoffice.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-style-human
openoffice.org-thesaurus-en-us
openoffice.org-writer
openprinting-ppds
openssh-client
openssl
openssl-blacklist
parted
passwd
pciutils
pcmciautils
perl
perl-base
perl-modules
pidgin
pidgin-data
pidgin-otr
pm-utils
pnm2ppa
policykit
policykit-gnome
poppler-utils
popularity-contest
powermanagement-interface
powermgmt-base
powernowd
ppp
pppconfig
procps
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11
pulseaudio-utils
pxljr
python
python-alsaaudio
python-apport
python-apt
python-awn
python-awn-extras
python-awnlib
python-beagle
python-brlapi
python-cairo
python-central
python-chardet
python-compizconfig
python-cups
python-cupshelpers
python-dateutil
python-dbus
python-debian
python-feedparser
python-gconf
python-gdata
python-gdbm
python-glade2
python-gmenu
python-gnome2
python-gnome2-desktop
python-gnomecanvas
python-gnupginterface
python-gobject
python-gst0.10
python-gtk2
python-gtkhtml2
python-gtksourceview2
python-imaging
python-launchpad-bugs
python-launchpad-integration
python-libxml2
python-minimal
python-newt
python-notify
python-numeric
python-pkg-resources
python-problem-report
python-pyatspi
python-pyorbit
python-rdflib
python-sexy
python-smbc
python-software-properties
python-sqlalchemy
python-support
python-tk
python-uno
python-usb
python-virtkey
python-vte
python-xapian
python-xdg
python-xkit
python-xlib
python2.5
python2.5-minimal
python2.6
python2.6-minimal
radeontool
raptor-utils
readahead
readline-common
redland-utils
rhythmbox
rss-glx
rsync
samba-common
sane-utils
scim
scim-gtk2-immodule
scim-modules-socket
screen
screen-profiles
screen-resolution-extra
seahorse
seahorse-plugins
shared-mime-info
smartdimmer
smbclient
software-properties-gtk
splix
sqlite3
ssh-askpass-gnome
ssl-cert
strace
sudo
synaptic
sysklogd
system-config-printer-common
system-config-printer-gnome
system-tools-backends
sysv-rc
sysvinit-utils
tangerine-icon-theme
tasksel
tasksel-data
tcl8.5
tcpd
tcpdump
telnet
thunderbird
time
tk8.4
tk8.5
tomboy
toshset
totem
totem-common
totem-gstreamer
totem-mozilla
totem-plugins
tracker
tracker-search-tool
tracker-utils
transmission-common
transmission-gtk
tsclient
ttf-arphic-uming
ttf-dejavu-core
ttf-kochi-gothic
ttf-kochi-mincho
ttf-liberation
ttf-opensymbol
ttf-sazanami-mincho
ttf-thai-tlwg
tzdata
ubufox
ubuntu-docs
ubuntu-gdm-themes
ubuntu-minimal
ubuntu-standard
ubuntu-system-service
ubuntu-wallpapers
ucf
udev
ufw
unattended-upgrades
uno-libs3
unzip
update-inetd
update-manager
update-manager-core
update-motd
update-notifier
update-notifier-common
ure
usb-creator
usplash
usplash-theme-ubuntu
util-linux
uuid-runtime
vbetool
vim-common
vim-tiny
vinagre
vino
wamerican
wbritish
wget
whiptail
whois
winbind
wine
wireless-crda
wireless-tools
wodim
wpasupplicant
wv
x-ttcidfont-conf
x11-apps
x11-common
x11-utils
x11-xfs-utils
x11-xkb-utils
x11-xserver-utils
xbase-clients
xdg-user-dirs-gtk
xdg-utils
xinput
xkb-data
xml-core
xorg
xsane
xsane-common
xserver-common
xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-kbd
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-geode
xserver-xorg-video-i128
xserver-xorg-video-i740
xserver-xorg-video-intel
xserver-xorg-video-mach64
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-r128
xserver-xorg-video-radeon
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-v4l
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo
xsltproc
xterm
xulrunner-1.9
xulrunner-1.9-gnome-support
yelp
zenity
zlib1g

---

### Post by bngguy on 2009-04-24
It seems more like a network issue, how is your system connected to the internet???, your last resort would be upgrading using an alternate CD/DVD

Please Note i have not tried this method, i just upgraded over the network and it worked for me.

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1. Download the alternate installation CD
   2. Burn the ISO to a CD and insert it into the CD-ROM drive of the  computer to be upgraded.
     * If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.

   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

---

