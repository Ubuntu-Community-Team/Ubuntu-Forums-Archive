---
title: "Broken Packages In Live CD Customization"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by js71296 on 2009-08-05
I am a developer and am customizing the Live CD, I still am fairly new to it all :). Anyway, I am building a LXDE Based system for older computers. I did not want gnome, so i removed it via this command:

 sudo apt-get remove alacarte app-install-data-partner apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk contact-lookup-applet dcraw desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-codec-install gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-canberra gnome-settings-daemon gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme indicator-applet indicator-messages jockey-gtk language-selector libart2.24-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcroco3 libcryptui0 libdecoration0 libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd-alsa0 libespeak1 libevdocument1 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.24-cil libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2a-cil libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.24-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomepanel2.24-cil libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod-common libgpod4 libgsf-1-114 libgsf-1-common libgsm1 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libindicate1 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal3.6.1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpt2.6.1 libpt2.6.1-plugins-alsa libpt2.6.1-plugins-v4l2 libpulse-browse0 libpulsecore9 libpurple-bin libpurple0 librarian0 librsvg2-2 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libsgutils1 libshout3 libsilc-1.1-2 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libv4l-0 libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwmf0.2-7-gtk libwnck-common libwnck22 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-2.0-runtime mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-libnotify pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-brlapi python-cairo python-fstab python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sg3-utils sgml-data software-properties-gtk ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers update-manager update-notifier usb-creator usplash-theme-ubuntu vinagre vino whois xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity

 Now, when ever i try to install something, I get this error,
 invoke-rc.d: initscript pulseaudio, action "start" failed.
dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
Setting up system-tools-backends (2.6.0-2ubuntu ...
invoke-rc.d: initscript dbus, action "force-reload" failed.
invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pulseaudio
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)


 I have tried apt-get install -f to get this same error... I need some help with this!!!

---

### Post by slakkie on 2009-08-05
I haven't tested it, but maybe you should have removed the following packages:

```

apt-cache -i depends ubuntu-desktop | awk '{print $NF}'

```

I would try to reinstall all packages you just tried to remove and start over.. 

BTW, next time when you do an action with so many packages:

aptitude -s remove|purge

-s is simulate, so you can see what will happen..

---

### Post by js71296 on 2009-08-06
thanks for the info slakkie, i am just going to restart because I can't work with APT anyway!

---

### Post by Lukios on 2009-09-24
How about your start with a mini.iso . . . just makes more sense. It will only include the barebones system allowing you to add what you want,

xorg
lxde

Along with other packages you will need. However, if you insist on using a full installation disk there you can refer to this page here. 

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

