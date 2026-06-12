---
title: "upgrades"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by cruzin on 2009-08-12
Hi 
i've been having trouble when i try and download and update software.
the following is the type of error message i get.My internet connection is fine so i am confused as to why i cant dowload. I was trying to update to ubuntu 8.10
:confused:




W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


cruzin

---

### Post by slakkie on 2009-08-12
Can you please tell me what you did (eg, which command did you type)?

Since I find it really weird that it's trying to connect with localhost port 4001 while you need to connect to archive.ubuntu.com...

Do you have http_proxy or ftp_proxy env. vars??

---

### Post by pizza-is-good on 2009-08-12
What version are you trying to upgrade from?

---

### Post by cruzin on 2009-08-12
i am realy  a beginner
i went to system,updatemanger,install update 8.10. it starts to download and then stops and says cant connect to host with the above details.

trying to upgrade from 8.04lts
cruzin

---

### Post by slakkie on 2009-08-12
Can you check your network settings in update-manager? I think you have some kind of proxy defined, which you are not running.

Or.. open a terminal (since I don't suspect proxy settings defined there):

```

# tell ubuntu that we are not upgrading lts to lts
echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
# Get updates from our repo's and see what we can upgrade
sudo aptitude update && sudo aptitude -s safe-upgrade
# if you are happy with the results
# Do the upgrade
sudo aptitude -y safe-upgrades
# Install a dependecy
sudo aptitude update-manager-core
# Update to 8.10
sudo do-release-upgrade

```

To upgrade to 9.04 from 8.10, redo the actions except the first line, that one is not needed.

---

### Post by cruzin on 2009-08-13
> **slakkie said:**
> Can you check your network settings in update-manager? I think you have some kind of proxy defined, which you are not running.

Or.. open a terminal (since I don't suspect proxy settings defined there):

```

# tell ubuntu that we are not upgrading lts to lts
echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
# Get updates from our repo's and see what we can upgrade
sudo aptitude update && sudo aptitude -s safe-upgrade
# if you are happy with the results
# Do the upgrade
sudo aptitude -y safe-upgrades
# Install a dependecy
sudo aptitude update-manager-core
# Update to 8.10
sudo do-release-upgrade

```

To upgrade to 9.04 from 8.10, redo the actions except the first line, that one is not needed.
i still noticed the error message listed below when i inputed the first part of the code?


network proxy is set at direct internet connection.

what do you suggest.


cruzin






hermit@hermit-desktop:~$ # tell ubuntu that we are not upgrading lts to lts
hermit@hermit-desktop:~$ echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
Prompt=normal
hermit@hermit-desktop:~$ # Get updates from our repo's and see what we can upgrade
hermit@hermit-desktop:~$ sudo aptitude update && sudo aptitude -s safe-upgrade
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  python-setuptools 
The following packages have been automatically kept back:
  language-support-writing-en 
The following packages have been kept back:
  bind9-host dnsutils f-spot libbind9-30 libisccc30 libisccfg30 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic ssl-cert 
The following packages will be upgraded:
  acpi-support acpid alacarte anacron app-install-data 
  app-install-data-commercial apparmor apparmor-utils apport apport-gtk apt 
  apt-utils avahi-autoipd avahi-daemon base-files bash bsdutils 
  capplets-data compiz compiz-core compiz-fusion-plugins-main compiz-gnome 
  compiz-plugins console-setup cpp cpp-4.2 cron cupsys cupsys-bsd 
  cupsys-client cupsys-common dash dbus dbus-x11 deskbar-applet 
  desktop-file-utils dhcp3-client dhcp3-common doc-base dpkg eject eog 
  evince evolution evolution-common evolution-data-server 
  evolution-data-server-common evolution-exchange evolution-plugins file 
  file-roller firefox firefox-3.0 firefox-3.0-gnome-support 
  firefox-gnome-support flashplugin-nonfree foo2zjs foomatic-filters 
  friendly-recovery gcalctool gcc gcc-4.2 gcc-4.2-base gcj-4.2-base gdb gdm 
  gedit gedit-common ghostscript ghostscript-x gij gij-4.2 gksu gnome-about 
  gnome-app-install gnome-applets gnome-applets-data gnome-cards-data 
  gnome-control-center gnome-desktop-data gnome-games gnome-games-data 
  gnome-keyring gnome-menus gnome-panel gnome-panel-data 
  gnome-power-manager gnome-settings-daemon gnome-system-monitor 
  gnome-system-tools gparted grub gs-gpl gstreamer0.10-esd 
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good 
  gstreamer0.10-plugins-ugly gstreamer0.10-tools gthumb gtk2-engines 
  gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks 
  gtkhtml3.14 guidance-backends gvfs gvfs-backends gvfs-fuse hal hal-info 
  hpijs hplip hplip-data initramfs-tools initscripts iproute jockey-common 
  jockey-gtk kdelibs-data kdelibs4c2a klibc-utils language-pack-ar 
  language-pack-ar-base language-pack-bn language-pack-bn-base 
  language-pack-de language-pack-de-base language-pack-en 
  language-pack-en-base language-pack-es language-pack-es-base 
  language-pack-fr language-pack-fr-base language-pack-gnome-ar 
  language-pack-gnome-ar-base language-pack-gnome-bn 
  language-pack-gnome-bn-base language-pack-gnome-de 
  language-pack-gnome-de-base language-pack-gnome-en 
  language-pack-gnome-en-base language-pack-gnome-es 
  language-pack-gnome-es-base language-pack-gnome-fr 
  language-pack-gnome-fr-base language-pack-gnome-hi 
  language-pack-gnome-hi-base language-pack-gnome-pt 
  language-pack-gnome-pt-base language-pack-gnome-xh 
  language-pack-gnome-xh-base language-pack-hi language-pack-hi-base 
  language-pack-pt language-pack-pt-base language-pack-xh 
  language-pack-xh-base libarts1c2a libartsc0 libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 
  libavahi-core5 libavahi-glib1 libavahi-qt3-1 libavahi-ui0 libavcodec1d 
  libavformat1d libavutil1d libc6 libc6-i686 libcairo2 libcamel1.2-11 
  libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdbus-1-3 
  libdecoration0 libdeskbar-tracker libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libfaad0 libffi4 libfreetype6 libgadu3 
  libgcc1 libgcj-bc libgcj-common libgcj8-1 libgdata-google1.2-1 
  libgdata1.2-1 libgksu2-0 libglib2.0-0 libglibmm-2.4-1c2a 
  libgnome-desktop-2 libgnome-keyring0 libgnome-menu2 
  libgnome-window-settings1 libgnomeui-0 libgnomeui-common libgnutls13 
  libgomp1 libgphoto2-2 libgphoto2-port0 libgs8 libgstreamer0.10-0 
  libgtk-vnc-1.0-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common 
  libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 
  libicu38 libisc32 libjasper1 libklibc libkrb53 liblcms1 libldap-2.4-2 
  liblircclient0 liblwres30 libmagic1 libmagick++10 libmagick10 
  libmysqlclient15off libnautilus-extension1 libnm-glib0 libnm-util0 
  libnspr4-0d libnss3-0d libnss3-1d libntfs-3g23 libpam-gnome-keyring 
  libpam-modules libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 
  libpango1.0-common libparted1.7-1 libpcre3 libpcrecpp0 libperl5.8 
  libpng12-0 libpolkit-gnome0 libpoppler-glib2 libpoppler2 libpostproc1d 
  libpulse-browse0 libpulse0 libpulsecore5 libpurple0 libruby1.8 libsasl2-2 
  libsasl2-modules libsdl-mixer1.2 libsmbclient libsmbios1 libsndfile1 
  libsnmp-base libsnmp15 libsoundtouch1c2 libsoup2.4-1 libspeex1 
  libssl0.9.8 libstdc++6 libtiff4 libtotem-plparser10 libtracker-gtk0 
  libtrackerclient0 libvolume-id0 libvorbis0a libvorbisenc2 libvorbisfile3 
  libwmf0.2-7 libwnck-common libwnck22 libxml2 libxml2-utils libxslt1.1 
  linux-restricted-modules-common login logrotate lsb-base lsb-release lshw 
  module-init-tools mount myspell-en-gb myspell-en-us myspell-en-za 
  mysql-common nautilus nautilus-data nautilus-sendto nautilus-share 
  network-manager network-manager-gnome notification-daemon ntfs-3g ntpdate 
  openoffice.org openoffice.org-base openoffice.org-base-core 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb 
  openoffice.org-help-en-us openoffice.org-impress 
  openoffice.org-java-common openoffice.org-l10n-common 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-officebean openoffice.org-style-human 
  openoffice.org-thesaurus-en-us openoffice.org-writer 
  openoffice.org-writer2latex openssh-client openssl parted passwd pciutils 
  perl perl-base perl-modules pidgin pidgin-data pm-utils policykit-gnome 
  poppler-utils procps pulseaudio pulseaudio-esound-compat 
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 
  pulseaudio-utils python-apport python-apt python-central python-crypto 
  python-gmenu python-gnome2-extras python-gobject python-gtkhtml2 
  python-launchpad-bugs python-libxml2 python-problem-report python-uno 
  python-virtkey python2.5 python2.5-minimal rdesktop readahead rhythmbox 
  ruby1.8 samba-common seahorse smbclient ssh-askpass-gnome sudo 
  sun-java6-bin sun-java6-jre sun-java6-plugin sysv-rc sysvutils tasksel 
  tasksel-data thunderbird-locale-en-gb tk8.4 tomboy totem totem-common 
  totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool 
  transmission-common transmission-gtk ttf-opensymbol tzdata ubuntu-docs 
  udev ufw update-manager update-manager-core update-notifier 
  update-notifier-common util-linux util-linux-locales vim-common vim-tiny 
  vinagre vino vorbis-tools wesnoth wesnoth-data x11-common xbase-clients 
  xfonts-scalable xkb-data xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-video-all xserver-xorg-video-amd 
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-geode 
  xserver-xorg-video-intel xserver-xorg-video-nsc xsltproc xterm 
  xulrunner-1.9 xulrunner-1.9-gnome-support xutils yelp 
445 packages upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
Need to get 428MB of archives. After unpacking 8909kB will be used.
Do you want to continue? [Y/n/?]

---

### Post by cruzin on 2009-08-16
> **slakkie said:**
> Can you check your network settings in update-manager? I think you have some kind of proxy defined, which you are not running.

Or.. open a terminal (since I don't suspect proxy settings defined there):

```

# tell ubuntu that we are not upgrading lts to lts
echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
# Get updates from our repo's and see what we can upgrade
sudo aptitude update && sudo aptitude -s safe-upgrade
# if you are happy with the results
# Do the upgrade
sudo aptitude -y safe-upgrades
# Install a dependecy
sudo aptitude update-manager-core
# Update to 8.10
sudo do-release-upgrade

```

To upgrade to 9.04 from 8.10, redo the actions except the first line, that one is not needed.
well our son was down and figured out what was wrong. it seems that when your running anon proxy you cant update. when we disabled anon proxy we were able to update.

hope this helps anyone else out there it seems several people were having the same problem
thanks to everyone
cruzin

---

### Post by slakkie on 2009-08-16
So you were running a proxy. Good to know everything is fixed now!

---

### Post by cruzin on 2009-08-16
evedentially. and i had now idea

---

