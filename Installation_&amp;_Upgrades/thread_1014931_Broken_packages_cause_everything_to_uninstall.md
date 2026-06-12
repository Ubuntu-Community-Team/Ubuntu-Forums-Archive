---
title: "Broken packages cause everything to uninstall"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Sugz on 2008-12-18
I have 5 Broken packages.

they are as follows.

gnome2-globalmenu-applet
GTK 2.0-Examples
gtk2-engines-pixbuf
libgtk2.0-0
libgtk2.0-bin

However when ever i mark each one uninstallation, virtually my entire system is marked for uninstallation?! 

This is weird and very annoying.. i just want to fix a tiny portion of my system not the entire thing!:mad:

---

### Post by gjoellee on 2008-12-18
> **Sugz said:**
> I have 5 Broken packages.

they are as follows.

gnome2-globalmenu-applet
GTK 2.0-Examples
gtk2-engines-pixbuf
libgtk2.0-0
libgtk2.0-bin

However when ever i mark each one uninstallation, virtually my entire system is marked for uninstallation?! 

This is weird and very annoying.. i just want to fix a tiny portion of my system not the entire thing!:mad:
 have you tried to install them?

those packages in needed for GNOME, and thats why more or less the whole system will be removed if those packages does...

---

### Post by Sugz on 2008-12-18
I cannot install them, i can only remove them according to synaptics
Oh and also, this has only been a problem when installing the Global-menu applet (wish i had not bothered now :( )
it may have something to do with the GTK patch or something that is needed for global menu.

---

### Post by Sugz on 2008-12-19
Here is my Terminal Output when i type in 
Sudo apt-get install -f

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  x11proto-resource-dev libcommons-collections3-java python-zopeinterface
  python-twisted-core libgsf-gnome-1-114 liblzo1 libcommons-pool-java
  libglitz-glx1 libsigc++-2.0-dev libgoffice-0-common
  gstreamer0.10-fluendo-mpegdemux libatk1.0-dev libgconf2-ruby liblucene-java
  python-clientform mplayer-skins gnome-pkg-tools libots0 python-twisted-web
  libcommons-el-java fftw3 libpango1.0-dev python-pygame junit
  libhal-storage-dev python-gdata libregexp-java libtagc0
  libcommons-modeler-java libatk1-ruby1.8 liblog4j1.2-java python-twill
  gnumeric-common python-mechanize psemu-drive-cdrmooby libseda-java
  psemu-sound-alsa libcommons-cli-java libtomcat5.5-java
  libstartup-notification0-dev libdvbpsi4 libmono-cairo2.0-cil
  python-configobj libxosd2 link-grammar-dictionaries-en python-bluez
  python-beautifulsoup libbcel-java psemu-sound-oss libvlc0 psemu-input-padjoy
  libcairomm-1.0-dev python-celementtree ant python-qt3
  libcommons-launcher-java libgnomescanui-common libwpd-stream8c2a
  libbonobo2-dev python-imaging libt1-5 vlc-nox python-mutagen libggi2
  libfltk1.1 libglibmm-2.4-dev gnome-common libgii1 python-daap libgdome2-0
  libwxbase2.6-0 nautilus-script-manager libgconf2-ruby1.8 python-louie
  python-pylirc libcommons-dbcp-java libglitz1 libglib2-ruby1.8 libtunepimp5
  python-pysqlite2 libifp4 libgii1-target-x libcairo-ruby1.8
  libcommons-collections-java libcroco3-dev libdvdnav4
  libcommons-beanutils-java libiso9660-4 thunar-data libgnomevfs2-dev
  libhal-dev python-pyparsing libgsf-1-dev libsdl-mixer1.2 python-coherence
  gstreamer0.10-flv libgdome2-cpp-smart0c2a libgnomescan-common
  libcommons-digester-java libselinux1-dev liblink-grammar4 libgconfmm-2.6-1c2
  libtar liblucene-java-doc libxres-dev libjsch-java libgnome2-dev
  libavahi-glib-dev ant-optional libsepol1-dev libvcdinfo0 libgsf0.0-cil
  libebml0 xfdesktop4-data python-twisted-bin libpango1-ruby1.8 libmx4j-java
  libmatroska0 psemu-video-x11 libnjb5 libofa0 python-kde3 python-gobject-dev
  libsdl-image1.2 libxine1-console libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-common gnome-pkg-tools
Recommended packages:
  svn-buildpackage
The following packages will be REMOVED
  alacarte amarok amarok-xine apport-gtk apturl arandr at-spi
  avant-window-navigator-bzr avg75fld awn-core-applets-bzr awn-manager-bzr
  azureus bluez-gnome brasero brltty-x11 bug-buddy cairo-dock
  cairo-dock-plug-ins compiz-plugins contact-lookup-applet deskbar-applet
  displayconfig-gtk eclipse-platform eclipse-rcp elisa-core elisa-extra
  elisa-plugins-bad elisa-plugins-good elisa-plugins-ugly emerald eog evince
  evolution-webcal f-spot fast-user-switch-applet file-browser-applet
  file-roller firefox firefox-gnome-support flegita gcalctool gconf-editor
  gdebi gdm gedit gedit-plugins ghex gimmie gimp gimp-print gimp-python gksu
  gnochm gnome-about gnome-accessibility-themes gnome-alsamixer
  gnome-app-install gnome-applets gnome-btdownload gnome-color-chooser
  gnome-control-center gnome-do gnome-games gnome-icon-theme gnome-keyring
  gnome-keyring-manager gnome-mag gnome-main-menu gnome-media gnome-menus
  gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-randr-applet
  gnome-screensaver gnome-session gnome-spell gnome-splashscreen-manager
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes
  gnome-user-guide gnome-utils gnome-volume-manager gnome2-globalmenu-applet
  gnumeric-gtk gparted gqview grandr graphicsmagick
  graphicsmagick-imagemagick-compat gstreamer0.10-plugins-good gsynaptics
  gthumb gtk2-engines gtk2-engines-aurora gtk2-engines-murrine
  gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtk2-engines-xfce
  gtk2.0-examples gtkhtml3.14 gucharmap hal-cups-utils hal-device-manager
  human-theme hwdb-client-gnome inkscape language-selector language-support-en
  libaiksaurusgtk-1.2-0c2a libatspi1.0-0 libawn0-bzr libbonoboui2-0
  libbonoboui2-dev libdeskbar-tracker libedataserverui1.2-8 libeel2-2
  libemeraldengine0 libexchange-storage1.2-3 libexo-0.3-0 libgail-common
  libgail-dev libgail-gnome-module libgail18 libgconf2.0-cil
  libgconfmm-2.6-dev libgdk-pixbuf2-ruby1.8 libgdl-1-0 libgdl-gnome-1-0
  libgimp2.0 libgksu2-0 libgksuui1.0-1 libglade2-0 libglade2-dev
  libglade2-ruby libglade2-ruby1.8 libglade2.0-cil libglademm-2.4-1c2a
  libgnome-desktop-2 libgnome-desktop-dev libgnome-keyring-dev
  libgnome-keyring0 libgnome-window-settings-dev libgnome-window-settings1
  libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomecanvas2-dev libgnomekbd1 libgnomekbdui1 libgnomemm-2.6-1c2a
  libgnomemm-2.6-dev libgnomeprintui2.2-0 libgnomescan0 libgnomescanui0
  libgnomeui-0 libgnomeui-dev libgoffice-gtk-0-4 libgpod2 libgraphicsmagick1
  libgtk2-perl libgtk2-ruby1.8 libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-dev libgtkglext1 libgtkglext1-dev libgtkhex0 libgtkhtml2-0
  libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmathview0c2a
  libgtkmm-2.4-1c2a libgtkmm-2.4-dev libgtksourceview1.0-0
  libgtksourceview2.0-0 libgtkspell0 libgucharmap6 libgutenprintui2-1
  liblaunchpad-integration0 liblpint-bonobo0 libmetacity-dev libmetacity0
  libnautilus-burn4 libnautilus-extension1 libnotify1 libpanel-applet2-0
  libpanel-applet2-dev libpanelappletmm-2.6-1c2 libpanelappletmm-2.6-dev
  libpigment0.3-4 libpoppler-glib2 librsvg2-2 librsvg2-common librsvg2-dev
  librsvg2.0-cil libsexy2 libslab0 libswt3.2-gtk-java libswt3.2-gtk-jni
  libthunar-vfs-1-2 libtotem-plparser7 libtracker-gtk0 libvte9 libwmf0.2-7
  libwnck-dev libwnck22 libwv-1.2-3 libwxgtk2.6-0 libxfcegui4-4 libxine1-gnome
  libxine1-plugins lightning-extension linuxdcpp metacity mousepad
  mozilla-firefox-locale-en-gb mozilla-mplayer mozilla-thunderbird mplayer
  nautilus nautilus-cd-burner nautilus-script-audio-convert nautilus-sendto
  nautilus-setup-background network-manager-gnome notification-daemon onboard
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human
  openoffice.org-thesaurus-en-us openoffice.org-writer orage pcsx pcsx-bin
  pidgin planner python-at-spi python-avahi python-awn-bzr python-beagle
  python-exo python-glade2 python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gpod python-gtk2
  python-gtk2-dev python-gtkglext1 python-gtkhtml2
  python-launchpad-integration python-notify python-pigment
  python-pygtksourceview python-sexy python-uno python-virtkey python-vte
  restricted-manager rhythmbox scim scim-gtk2-immodule scim-modules-table
  scim-tables-additional screenlets screensaver-default-images sensors-applet
  serpentine software-properties-gtk sound-juicer soundconverter
  ssh-askpass-gnome synaptic system-config-printer tagtool
  tangerine-icon-theme tango-icon-theme-common thunar thunar-archive-plugin
  thunar-media-tags-plugin thunar-volman thunderbird thunderbird-locale-en-gb
  tomboy totem totem-mozilla totem-xine tracker tracker-search-tool
  tracker-utils tsclient ubufox ubuntu-artwork ubuntu-docs update-manager
  update-notifier usp2 vino vlc wbarconf xchm xdg-user-dirs-gtk
  xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin
  xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer
  xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin
  xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin
  xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin
  xfce4-weather-plugin xfce4-xfapplet-plugin xfce4-xkb-plugin xfdesktop4
  xfprint4 xfwm4 xfwm4-themes xsane xscreensaver-data xscreensaver-gl
  xubuntu-desktop yelp zenity
The following NEW packages will be installed
  gnome-common gnome-pkg-tools
0 upgraded, 2 newly installed, 364 to remove and 44 not upgraded.
4 not fully installed or removed.
Need to get 46.5kB of archives.
After unpacking 1184MB disk space will be freed.
Do you want to continue [Y/n]? n 
Abort.

```

So in other words, virtually my entire system. I do not want to execute this command, otherwise i will lose everything!

---

### Post by Kevbert on 2008-12-19
Have you tried the following in terminal ?
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
```

---

### Post by Sugz on 2008-12-19
Those commands sounds very destructive to me. 
I am not able to connect my laptop to the net at the moment, but when i run

sudo dpkg --configure -a

i get

errors were encountered while processing:
gtk2.0-examples
gtk2-engines-pixbuf
gnome2-globalmenu-applet
libgtk2.0-bin

Look above for the output of 
sudo apt-get install -f

and i believe the third command installs the latest build of ubuntu no?

Im not going to run any command which could risk me loosing all of my hard work in configuring ubuntu to the way i like it. sorry

---

### Post by Kevbert on 2008-12-19
The second command does a forced repair of packages, sorry, I missed that in your previous post. The third will just update the package list.
What version of Ubuntu are you using ? You can get that via
```
uname -a
```
You may want to try to re-install those packages via Synaptic. If you try just one package say the examples package and see if by right-clicking on the package, Mark for re-installation and then Apply.

---

### Post by markbuntu on 2008-12-19
Synaptic has "fix broken packages" option on the menus somewhere. That usually works for me.

---

### Post by jimjutte on 2008-12-19
Okay... I was actually stupid enough not to notice it remove pretty much the entire system. Any suggestions on how to bring it back?

I was using 8.10 when, I made the error. I forgot to burn a CD/DVD and now only have 8.04... I am running off of the CD right now. I would just reintall, but I have personal file (I hope) that I do not want to delete.

When I look at the partitions on the HDD from the 8.04 gui view... the folders all seem intact. Is it possible to just pull off the package from ubuntu.com and install them in the terminal view?

I tried a simple sudo apt-get upgrade, but that shows that is it not picking up anything... I assume because there is nothing to upgrade.

Cheers

---

### Post by markbuntu on 2008-12-19
You can install/reinstall without losing your /home. Just don't change your partitions and uncheck format in the partitioner during the install process and it will leave your /home alone. The install should overwrite the files it needs to and leave your data intact.

---

### Post by Sugz on 2008-12-21
Right, i have a net connectio back again. 
From my understanding, the command which does a forced repair of broken packages in my case simply uninstalls Everything.
I have a feeling that this is going to be a very Long and painfull process of reinstalling. Well i think i have just exposed something that sucks with Linux..
To answer a question, i cannot select re-install. 
Synaptics.. simply has the option to remove, thats it. It feels like synaptics is forcing me to wipe out my system

---

### Post by Sugz on 2008-12-21
FIXED!!!!!


How?

I ran the following in the terminal

Sudo Aptitude

What it did:
Aptitude identified the problem package. and removed it cleanly without destroying my system. 

Aptitude, you are my saviour!

---

