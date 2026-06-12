---
title: "[SOLVED] apt-get autoremove wants to uninstall most of my system"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by jenkinbr on 2008-12-18
Whenever I install packages by the command line, I always get a ton of suggested packages for autoremoval.  Of coarse, most of those packages I actually need or use on a regular basis.

Below is the output of 'sudo apt-get install autoremove':

```
jenkinbr@jenkinbr:~$ sudo apt-get autoremove 
[sudo] password for jenkinbr: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pipenightdreams python-crypto memaker gtkpool libpano13-bin hexter python-alsaaudio pwgen
  gstreamer0.10-plugins-bad-dbg gnome-do libclxclient3 python-zopeinterface dict-gcide
  brutalchess python-twisted-names ubuntustudio-graphics pipenightdreams-data python-awn-extras
  cssed python-twisted-core libzzip-0-13 alsa-tools pulseaudio-esound-compat-dbg lmms
  supertux-data guile-1.8 gtk-theme-switch sooperlooper crack-common gstreamer-tools
  texlive-base-bin-doc gstreamer0.10-plugins-base-dbg freebirth-data gnome-do-plugins
  gstreamer0.10-fluendo-mpegdemux scim-modules-table acroread-escript synfig-examples
  lilypond-doc rox-filer gnome-games-extra-data geekcode qamix libevolution3.0-cil libgcj8-1
  lilypond-data debram-data audacious enblend libportaudio2 gstreamer0.10-packagekit gamix tapiir
  cfi-en figlet module-assistant texlive-base alsa-firmware-loaders tea-data qjackctl terminatorx
  libimage-exiftool-perl texlive lvm2 bumprace libbinio1ldbl texlive-fonts-recommended opencity
  blast fortunes-spam texlive-pstricks-doc freqtweak libjinglebase0.3-0 pinball-data topshelf
  gtick memstat dssi-example-plugins libots0 python-twisted-web gnome-network-admin libaudclient1
  devilspie libresid-builder0c2a pulseaudio-module-zeroconf-dbg lmodern dictzip muse csound
  libftgl2 blubuntu-gdm-theme cairo-dock qstat ocaml-base-nox python-twisted-runner paprefs
  shaketracker libaiksaurusgtk-1.2-0c2a abiword-common supertux ubuntustudio-audio-plugins purity
  smbfs asoundconf-gtk libjack0.100.0-0 lmms-common freebirth abiword python-pymad
  abiword-plugin-mathview linux-restricted-modules-2.6.27-8-generic latex-xft-fonts
  texlive-common pysdm awn-applets-python-core dssi-utils scim-tables-additional rats denemo
  libaiksaurus-1.2-0c2a libqt3-i18n libqt4-core libchm1 vodovod mc python-pyogg python-chm
  doc-linux-text libcddb2 community-themes libgcj8-jar bitscope mhwaveedit flake
  libboost-thread1.34.1 gstreamer-dbus-media-service python-awn libdv-bin dict-wn libtsmux0
  dict-vera libpulse-mainloop-glib0 libdjconsole0 pulseaudio-module-gconf-dbg alsa-oss puredata
  crack-md5 acroread-plugins mscore mountmanager debconf-utils psemu-drive-cdrmooby
  libjinglexmllite0.3-0 polygen mysqltuner audacious-plugins psemu-sound-alsa texlive-pstricks
  extremetuxracer-data genpo maint-guide libcsound64-5.1 planetpenguin-racer-extras
  python-utidylib libsnack2 texlive-base-bin bristol libsdl-net1.2 csound-gui polygen-data
  dssi-host-jack pavucontrol foobillard cairo-dock-data libxosd2 alsaplayer-alsa libloudmouth1-0
  fontforge link-grammar-dictionaries-en python-pyvorbis tango-icon-theme-common tango-icon-theme
  extremetuxracer mscore-common libjinglep2p0.3-0 bumprace-data dvipdfmx python-serial tetex-bin
  libalut0 gnome-themes-extras atomix jackeq libgtkmm1.2-0c2a python-ogg python-pam
  psemu-sound-oss python-openssl python-twisted-mail wmscope dict-foldoc gnome-color-chooser
  jdelay psemu-input-padjoy hugin-data apg bse-alsa pstoedit libsynfigapp0 libsdl-sound1.2
  abiword-help prosper python-numpy gstreamer0.10-plugins-farsight blt tipa alsaplayer-text
  libk3b3-extracodecs pulseaudio-module-hal-dbg texlive-latex-recommended-doc python-tk samba-doc
  libawn-extras0 lightspeed texlive-latex-base-doc manedit libqt4-gui libgtkimageview0
  gcj-4.2-base ardour-i686 gstreamer0.10-plugins-ugly-dbg hugin gem synfigstudio
  libaiksaurus-1.2-data ubuntustudio-look libsynfig0 antiword libsdl-ttf2.0-0 libmikmod2 3dchess
  mixxx gstreamer0.10-plugins-good-dbg atomix-data libgdome2-0 python-pyao bash-doc
  libjinglexmpp0.3-0 ubuntustudio-sounds fluidsynth-dssi burn recite gnome-alsamixer
  abiword-plugin-grammar avant-window-navigator python-twisted-lore python-twisted-conch pinball
  dictd libxul0d gnome-raw-thumbnailer libaudid3tag1 libclthreads2 python-pyopenssl libgcj8-1-awt
  python-twisted-news python-feedparser python-twisted-words fluid-soundfont-gm
  fluid-soundfont-gs libphysfs-1.0-0 pulseaudio-module-x11-dbg avant-window-navigator-data
  jack-rack mixxx-data xdesktopwaves libsigc++-1.2-5c2 qsynth libwmf-bin python-twisted
  mirrormagic pgf awn-applets-c-core autopano-sift pulseaudio-module-lirc dict-jargon scribus
  flac gweled libspiro0 ubuntustudio-desktop fil-plugins libdjconsole-data samba libpano13-0
  libwnck2.20-cil gnome-humility-icon-theme acroread-l10n-de timemachine planetpenguin-racer
  texlive-latex-recommended acroread-l10n-en tea gstreamer0.10-plugins-bad-multiverse-dbg
  hydrogen libmowgli1 dpkg-awk libpackagekit8 lilypond ubuntustudio-theme libfluidsynth1
  jack-tools python-uniconvertor libportmidi0 texlive-generic-recommended debram stk packagekit
  fluidsynth aconnectgui fuseiso man2html tcl8.5 audacious-plugins-extra wavesurfer
  medibuntu-keyring planetpenguin-racer-data mylvmbackup beast libgeoip1 texlive-latex-base
  libsdl-mixer1.2 nexuiz-data gnome-specimen texlive-fonts-recommended-doc
  gstreamer0.10-fluendo-mp3 pulseaudio-module-zeroconf libxml++2.6-2 blender xqf
  libgdome2-cpp-smart0c2a alsaplayer-daemon libsidplay2 padevchooser paman tk707
  extremetuxracer-gimp-dev pulseaudio-module-lirc-dbg murrine-themes python-awnlib chmsee
  ubuntustudio-audio libaubio2 libstk0c2a alsaplayer-jack ubuntustudio-wallpapers libsigc++0c2
  pcsx-df mpg321 acroread-fonts grip seq24 mozilla-acroread psemu-input-omnijoy
  libconfig-inifiles-perl latex-beamer ubuntustudio-default-settings alsaplayer-xosd timidity
  gstreamer0.10-fluendo-mpegmux liblink-grammar4 xaw3dg packagekit-backend-apt
  gstreamer0.10-plugins-ugly-multiverse-dbg libgtkmathview0c2a mirrormagic-data
  app-install-data-medibuntu liblrdf0 patchage kernel-package creox qgtkstyle
  ubuntustudio-icon-theme libmcs1 alsaplayer-esd libuninameslist0 swami stops libpam-smbpass
  libxul-common apt-doc abiword-plugins libclalsadrv1 latex-xcolor acroread-dictionary-de jackd
  python-eyed3 acroread acroread-dictionary-en gstreamer0.10-sdl alsaplayer-gtk ladcca2
  acroread-debian-files oxygen-cursor-theme-extra fxload perlmagick viruskiller mountapp
  python-chardet gimp-ufraw pdftk pavumeter meterbridge rutebook alsaplayer-common inkscape
  texlive-doc-base jackbeat alsaplayer-nas libid3-3.8.3c2a libestools1.2 alsa-tools-gui
  tex-common python-twisted-bin pulseaudio-utils-dbg awn-manager psemu-video-x11 libnotify0.4-cil
  aeolus texinfo nexuiz gstreamer0.10-gnonlin-dev alsaplayer-oss nexuiz-music
  libgnomedesktop2.20-cil hugin-tools oxygen-cursor-theme alsamixergui csound-utils jamin
  libsmpeg0
The following packages will be REMOVED:
  3dchess abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview
  abiword-plugins aconnectgui acroread acroread-debian-files acroread-dictionary-de
  acroread-dictionary-en acroread-escript acroread-fonts acroread-l10n-de acroread-l10n-en
  acroread-plugins aeolus alsa-firmware-loaders alsa-oss alsa-tools alsa-tools-gui alsamixergui
  alsaplayer-alsa alsaplayer-common alsaplayer-daemon alsaplayer-esd alsaplayer-gtk
  alsaplayer-jack alsaplayer-nas alsaplayer-oss alsaplayer-text alsaplayer-xosd antiword apg
  app-install-data-medibuntu apt-doc ardour-i686 asoundconf-gtk atomix atomix-data audacious
  audacious-plugins audacious-plugins-extra autopano-sift avant-window-navigator
  avant-window-navigator-data awn-applets-c-core awn-applets-python-core awn-manager bash-doc
  beast bitscope blast blender blt blubuntu-gdm-theme bristol brutalchess bse-alsa bumprace
  bumprace-data burn cairo-dock cairo-dock-data cfi-en chmsee community-themes crack-common
  crack-md5 creox csound csound-gui csound-utils cssed debconf-utils debram debram-data denemo
  devilspie dict-foldoc dict-gcide dict-jargon dict-vera dict-wn dictd dictzip doc-linux-text
  dpkg-awk dssi-example-plugins dssi-host-jack dssi-utils dvipdfmx enblend extremetuxracer
  extremetuxracer-data extremetuxracer-gimp-dev figlet fil-plugins flac flake fluid-soundfont-gm
  fluid-soundfont-gs fluidsynth fluidsynth-dssi fontforge foobillard fortunes-spam freebirth
  freebirth-data freqtweak fuseiso fxload gamix gcj-4.2-base geekcode gem genpo gimp-ufraw
  gnome-alsamixer gnome-color-chooser gnome-do gnome-do-plugins gnome-games-extra-data
  gnome-humility-icon-theme gnome-network-admin gnome-raw-thumbnailer gnome-specimen
  gnome-themes-extras grip gstreamer-dbus-media-service gstreamer-tools gstreamer0.10-fluendo-mp3
  gstreamer0.10-fluendo-mpegdemux gstreamer0.10-fluendo-mpegmux gstreamer0.10-gnonlin-dev
  gstreamer0.10-packagekit gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-multiverse-dbg
  gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-sdl
  gtick gtk-theme-switch gtkpool guile-1.8 gweled hexter hugin hugin-data hugin-tools hydrogen
  inkscape jack-rack jack-tools jackbeat jackd jackeq jamin jdelay kernel-package ladcca2
  latex-beamer latex-xcolor latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data
  libaiksaurusgtk-1.2-0c2a libalut0 libaubio2 libaudclient1 libaudid3tag1 libawn-extras0
  libbinio1ldbl libboost-thread1.34.1 libcddb2 libchm1 libclalsadrv1 libclthreads2 libclxclient3
  libconfig-inifiles-perl libcsound64-5.1 libdjconsole-data libdjconsole0 libdv-bin libestools1.2
  libevolution3.0-cil libfluidsynth1 libftgl2 libgcj8-1 libgcj8-1-awt libgcj8-jar libgdome2-0
  libgdome2-cpp-smart0c2a libgeoip1 libgnomedesktop2.20-cil libgtkimageview0 libgtkmathview0c2a
  libgtkmm1.2-0c2a libid3-3.8.3c2a libimage-exiftool-perl libjack0.100.0-0 libjinglebase0.3-0
  libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 libk3b3-extracodecs liblink-grammar4
  libloudmouth1-0 liblrdf0 libmcs1 libmikmod2 libmowgli1 libnotify0.4-cil libots0 libpackagekit8
  libpam-smbpass libpano13-0 libpano13-bin libphysfs-1.0-0 libportaudio2 libportmidi0
  libpulse-mainloop-glib0 libqt3-i18n libqt4-core libqt4-gui libresid-builder0c2a libsdl-mixer1.2
  libsdl-net1.2 libsdl-sound1.2 libsdl-ttf2.0-0 libsidplay2 libsigc++-1.2-5c2 libsigc++0c2
  libsmpeg0 libsnack2 libspiro0 libstk0c2a libsynfig0 libsynfigapp0 libtsmux0 libuninameslist0
  libwmf-bin libwnck2.20-cil libxml++2.6-2 libxosd2 libxul-common libxul0d libzzip-0-13
  lightspeed lilypond lilypond-data lilypond-doc link-grammar-dictionaries-en
  linux-restricted-modules-2.6.27-8-generic lmms lmms-common lmodern lvm2 maint-guide man2html
  manedit mc medibuntu-keyring memaker memstat meterbridge mhwaveedit mirrormagic
  mirrormagic-data mixxx mixxx-data module-assistant mountapp mountmanager mozilla-acroread
  mpg321 mscore mscore-common murrine-themes muse mylvmbackup mysqltuner nexuiz nexuiz-data
  nexuiz-music ocaml-base-nox opencity oxygen-cursor-theme oxygen-cursor-theme-extra packagekit
  packagekit-backend-apt padevchooser paman paprefs patchage pavucontrol pavumeter pcsx-df pdftk
  perlmagick pgf pinball pinball-data pipenightdreams pipenightdreams-data planetpenguin-racer
  planetpenguin-racer-data planetpenguin-racer-extras polygen polygen-data prosper
  psemu-drive-cdrmooby psemu-input-omnijoy psemu-input-padjoy psemu-sound-alsa psemu-sound-oss
  psemu-video-x11 pstoedit pulseaudio-esound-compat-dbg pulseaudio-module-gconf-dbg
  pulseaudio-module-hal-dbg pulseaudio-module-lirc pulseaudio-module-lirc-dbg
  pulseaudio-module-x11-dbg pulseaudio-module-zeroconf pulseaudio-module-zeroconf-dbg
  pulseaudio-utils-dbg puredata purity pwgen pysdm python-alsaaudio python-awn python-awn-extras
  python-awnlib python-chardet python-chm python-crypto python-eyed3 python-feedparser
  python-numpy python-ogg python-openssl python-pam python-pyao python-pymad python-pyogg
  python-pyopenssl python-pyvorbis python-serial python-tk python-twisted python-twisted-bin
  python-twisted-conch python-twisted-core python-twisted-lore python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner python-twisted-web
  python-twisted-words python-uniconvertor python-utidylib python-zopeinterface qamix qgtkstyle
  qjackctl qstat qsynth rats recite rox-filer rutebook samba samba-doc scim-modules-table
  scim-tables-additional scribus seq24 shaketracker smbfs sooperlooper stk stops supertux
  supertux-data swami synfig-examples synfigstudio tango-icon-theme tango-icon-theme-common
  tapiir tcl8.5 tea tea-data terminatorx tetex-bin tex-common texinfo texlive texlive-base
  texlive-base-bin texlive-base-bin-doc texlive-common texlive-doc-base texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base
  texlive-latex-base-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-pstricks
  texlive-pstricks-doc timemachine timidity tipa tk707 topshelf ubuntustudio-audio
  ubuntustudio-audio-plugins ubuntustudio-default-settings ubuntustudio-desktop
  ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-sounds
  ubuntustudio-theme ubuntustudio-wallpapers viruskiller vodovod wavesurfer wmscope xaw3dg
  xdesktopwaves xqf
0 upgraded, 0 newly installed, 441 to remove and 0 not upgraded.
After this operation, 2079MB disk space will be freed.
Do you want to continue [Y/n]? no!!!
Abort.
jenkinbr@jenkinbr:~$ 

```

I will also include my /etc/apt/sources.list, even though I highly doubt that this has anything to do with my problem:

```

jenkinbr@jenkinbr:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted



deb file:///home/jenkinbr/setup/repo/ubuntu/ intrepid main multiverse restricted universe
deb file:///home/jenkinbr/setup/repo/ubuntu/ intrepid-updates main multiverse restricted universe
deb file:///home/jenkinbr/setup/repo/ubuntu/ intrepid-security main multiverse restricted universe
deb file:///home/jenkinbr/setup/repo/ubuntu/ intrepid-backports main multiverse restricted universe
deb file:///home/jenkinbr/setup/repo/ubuntu/ intrepid-proposed main multiverse restricted universe

deb file:///home/jenkinbr/setup/repo/medibuntu/ intrepid free non-free

deb file:///home/jenkinbr/setup/repo/ppa.launchpad.net/compiz/ubuntu intrepid main
deb file:///home/jenkinbr/setup/repo/ppa.launchpad.net/martin-espinoza/ubuntu intrepid main


```

Note that I run an offline installation of Ubuntu, and therefor cannot access the online repositories. I have to [download the repositorie]("https://help.ubuntu.com/community/AptGet/Offline/Repository")s and generate a download script using synaptic.

---

### Post by jenkinbr on 2008-12-18
bump

---

### Post by jenkinbr on 2008-12-19
anyone?

---

### Post by albinootje on 2008-12-19
There's something very wrong there.
Did you install ubuntustudio-desktop and/or ubuntu-desktop ?
Is it possible to go online somewhere and do an upgrade ?

---

### Post by |{urse on 2008-12-19
> Do you want to continue [Y/n]? no!!!



?

---

### Post by jenkinbr on 2008-12-19
I did install both packages (ubuntu-desktop was part of the ubuntu cd), while I had to install the ubuntustudio-desktop package seperatly because the computers I use to download have a maximum allowed modification space limit of ~1GB

It would be possible to bring the PC to a friend's house, but would be rather tedious to do.

Also, just though of this: could it have anything to do with using the aptoncd-metapackage to install software from the CDs that I make?

@|{urse: it only takes the first byte, everything else is ignored.  (I got bored)

---

### Post by albinootje on 2008-12-19
> **jenkinbr said:**
> I did install both packages (ubuntu-desktop was part of the ubuntu cd), while I had to install the ubuntustudio-desktop package seperatly because the computers I use to download have a maximum allowed modification space limit of ~1GB

It would be possible to bring the PC to a friend's house, but would be rather tedious to do.

Also, just though of this: could it have anything to do with using the aptoncd-metapackage to install software from the CDs that I make?

Do you actually have internet yourself at home or not at all ? Or is 1 Gb the internet download limit there ?

And i think there must be a conflict with the packages somewhere. 
Or you have managed to remove something which was so vital that apt-get now suggests to remove almost all packages.

---

### Post by jenkinbr on 2008-12-19
I don't have internet at home.  Currently I get all my internet access needs taken care of at the local college where I attend school.  They run WinXP with CenturianGuard to lock down the hdd's to prevent any changes made on the hdd from staying after the computer is rebooted.  Yhid involves the use of a swap file that stores the changes, rather than creating/modifying the actual file on disk.  1GB is the limit set on these swap files (not even sure if 'swap' is the right term here)

As I have noted above, I have used the aptoncd-metapackage 's, but then I remove them later.  Could this be part of the problem?

---

### Post by Bachstelze on 2008-12-19
Most likely the [font="monospace"]ubuntu-desktop[/font] package was uninstalled somehow. Try reinstalling it.

---

### Post by jenkinbr on 2008-12-19
> **HymnToLife said:**
> Most likely the [font="monospace"]ubuntu-desktop[/font] package was uninstalled somehow. Try reinstalling it.
I will check that out later.

In the meantime, I will start the process of an update just in case, so I can select it later if I need to...

---

### Post by jenkinbr on 2008-12-19
I checked and do have ubuntu-desktop and ubuntustudio-desktop installed.

If you want, have a look at my /var/lib/dpkg/status file. I uploaded it to mediafire as [status.txt]("http://www.mediafire.com/?sharekey=b62d7182861f4d7e91b20cc0d07ba4d2b4ce12b5cd38f42a") , as it is too large to upload to these forums (~2.2 MB)

---

### Post by |{urse on 2008-12-20
> **jenkinbr said:**
> I did install both packages (ubuntu-desktop was part of the ubuntu cd), while I had to install the ubuntustudio-desktop package seperatly because the computers I use to download have a maximum allowed modification space limit of ~1GB

It would be possible to bring the PC to a friend's house, but would be rather tedious to do.

Also, just though of this: could it have anything to do with using the aptoncd-metapackage to install software from the CDs that I make?

@|{urse: it only takes the first byte, everything else is ignored.  (I got bored)

lol right on.

---

### Post by jenkinbr on 2008-12-23
bump

---

### Post by unutbu on 2008-12-23
Does this help?
```
sudo aptitude keep-all
```

See [http://ubuntuforums.org/showthread.php?t=842399](http://ubuntuforums.org/showthread.php?t=842399)

---

### Post by jenkinbr on 2008-12-24
Did the trick.

Might need to install deborphan (or whatever it's called) if I uninstall anything, as doing that may leave extra stuff on the machine.

Thanks, unutbu. (I like how that sounds - oo-noot-boo :))

---

### Post by evilninja on 2009-02-05
Thanks for this hint, unutbu. Usually I try to avoid aptitude but this keep-all thingy did the trick. I fail to understand why, though. No packages were marked "deinstall", "deborphan --guess-all" returned nothing, but "apt-get install" always suggested to remove my Xen setup.

Thanks again, this has bothered me for quite a while now....
C.

---

### Post by jenkinbr on 2009-02-05
I think I had found a way to do it using apt-get when I was reading the manpages for it, but I can't remember...

Or not.

---

