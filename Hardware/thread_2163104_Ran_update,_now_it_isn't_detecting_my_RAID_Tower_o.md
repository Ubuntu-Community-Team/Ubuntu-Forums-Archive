---
title: "Ran update, now it isn't detecting my RAID Tower on reboot"
date: 2013-07-17
forum: Hardware
---

### Post by Seifer44 on 2013-07-17
Long story short: I needed to install a GUI so that I could get cgminer to run properly. I decided to get kubuntu's GUI.

```
sudo apt-get install xubuntu-desktop
```

It installed just fine, and I rebooted. The GUI loaded with no problems... at first.

In the GUI, I let it install some updates, then it requested to reboot.  So I did. No problems. It then wanted to install MORE updates, so I let  it. The GUI then requested to install updates for a 3rd time, without requesting for a reboot from the 2nd wave. I  installed them, and it rebooted. After the reboot, it says that it can't mount my RAID  tower. The UUID isn't even appearing in the system, nor is the RAID array showing  up under /dev.

I tried removing kubuntu-desktop, but that didn't fix the problem. It's  headless again. This is what I ran, upon the recommendation of [http://www.psychocats.net/ubuntu/pureubuntuprecise](http://www.psychocats.net/ubuntu/pureubuntuprecise)

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish  docbook-xml exo-utils flex fonts-droid gigolo gimp gimp-data  gmusicbrowser gnome-desktop-data gnome-system-tools gnome-time-admin  gnumeric gnumeric-common gnumeric-doc gstreamer0.10-gnomevfs gthumb  gthumb-data gtk2-engines-pixbuf indicator-application-gtk2  indicator-messages-gtk2 indicator-sound-gtk2  indicator-status-provider-pidgin leafpad libabiword-2.9 libao-common  libao4 libaudio-scrobbler-perl libbabl-0.0-0 libbison-dev libcolamd2.7.1  libconfig-inifiles-perl libdigest-crc-perl libencode-locale-perl  libept1.4.12 libexo-1-0 libexo-common libexo-helpers  libfile-listing-perl libfl-dev libfont-afm-perl libgarcon-1-0  libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0  libgimp2.0 libglade2-0 libgnomevfs2-0 libgnomevfs2-common  libgnomevfs2-extra libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114  libgsf-1-common libgstreamer-perl libgtk2-notify-perl  libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0  libido-0.1-0 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl  libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs  libkeybinder0 liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0  liblwp-mediatypes-perl liblwp-protocol-https-perl libmad0  libmailtools-perl libnet-dbus-perl libnet-http-perl libnet-ssleay-perl  liboobs-1-5 libopenexr6 libotr2 libots0 librarian0 libsexy2  libsocket6-perl libtagc0 libthunarx-2-0 libtidy-0.99-0  libtie-ixhash-perl libtimedate-perl libtumbler-1-0 libunique-1.0-0  liburi-perl libvte-common libvte9 libwebkitgtk-1.0-0  libwebkitgtk-1.0-common libwv-1.2-4 libwww-perl libwww-robotrules-perl  libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4  libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl  libxml-xpath-perl libxss1 lightdm-gtk-greeter  link-grammar-dictionaries-en linux-headers-3.2.0-24  linux-headers-3.2.0-24-generic linux-headers-generic lp-solve m4 mpg321  orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify  pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo  plymouth-theme-xubuntu-text python-configobj python-glade2 python-gmenu  rarian-compat ristretto screensaver-default-images sgml-data  shimmer-themes synaptic system-tools-backends tcl8.5 thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman  ttf-droid ttf-lyx tumbler tumbler-common xchat xchat-common xfburn  xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin  xfce4-datetime-plugin xfce4-dict xfce4-indicator-plugin  xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes  xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin  xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin  xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl  xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs  xubuntu-icon-theme xubuntu-wallpapers
```

I did not let it install the Unity desktop, though, hence why I clipped that statement.

I ran this for good measure. That long remove command got everything, according to the simple statement.
```
sudo apt-get --purge remove kubuntu-desktop
```

I autoremoved the rest of the data off.
```
sudo apt-get autoremove
```

Still can't get my RAID tower to detect. The tower has ***NOT***  failed at the exact same time I rebooted, since the RAID controller  shows the array just fine before the system boots. Tried unplugging  everything for a minute or two, but that didn't fix the problem.  Restarted a whole bunch of times, and that did nothing, either.

I'm not familiar with rolling back updates in Linux, nor am I sure which update had the issue.

I'm running 12.04.2 LTS 64-bit


Here's the output after running ```
cat /var/log/dpkg.log | egrep 'install |upgrade '

``````
2013-07-16 16:35:10 upgrade php5-cli 5.3.10-1ubuntu3.6 5.3.10-1ubuntu3.7
2013-07-16 16:35:13 upgrade php5-mysql 5.3.10-1ubuntu3.6 5.3.10-1ubuntu3.7
2013-07-16 16:35:15 upgrade php5-gd 5.3.10-1ubuntu3.6 5.3.10-1ubuntu3.7
2013-07-16 16:35:18 upgrade libapache2-mod-php5 5.3.10-1ubuntu3.6 5.3.10-1ubuntu3.7
2013-07-16 16:35:21 upgrade php5-common 5.3.10-1ubuntu3.6 5.3.10-1ubuntu3.7
2013-07-16 16:35:24 upgrade linux-headers-server 3.2.0.29.31 3.2.0.49.59
2013-07-16 16:35:26 upgrade php5 5.3.10-1ubuntu3.6 5.3.10-1ubuntu3.7
2013-07-16 16:36:42 install linux-image-3.2.0-49-generic <none> 3.2.0-49.75
2013-07-16 16:37:08 install libterm-readkey-perl <none> 2.30-4build3
2013-07-16 16:37:09 upgrade mysql-client-5.5 5.5.31-0ubuntu0.12.04.1 5.5.31-0ubuntu0.12.04.2
2013-07-16 16:37:12 upgrade mysql-server-5.5 5.5.31-0ubuntu0.12.04.1 5.5.31-0ubuntu0.12.04.2
2013-07-16 16:37:20 upgrade mysql-server-core-5.5 5.5.31-0ubuntu0.12.04.1 5.5.31-0ubuntu0.12.04.2
2013-07-16 16:37:22 upgrade linux-server 3.2.0.29.31 3.2.0.49.59
2013-07-16 16:37:23 upgrade linux-image-server 3.2.0.29.31 3.2.0.49.59
```

---

### Post by dannyboy79 on 2013-07-17
is this hardware raid or software raid? you say that the raid controller can see the array just fine before the system boots, what do you mean by that? what does this return?
```
sudo fdisk -l
```
that will give you information on your hard drives and each of their partition tables

---

### Post by Seifer44 on 2013-07-17
It's a hardware RAID. The controller boots before the BIOS screen, and it detects the RAID array just fine.

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT

Disk /dev/mapper/seifer--server-root: 991.7 GB, 991701237760 bytes
255 heads, 63 sectors/track, 120567 cylinders, total 1936916480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/seifer--server-root doesn't contain a valid partition table

Disk /dev/mapper/seifer--server-swap_1: 8044 MB, 8044675072 bytes
255 heads, 63 sectors/track, 978 cylinders, total 15712256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/seifer--server-swap_1 doesn't contain a valid partition table
```

---

