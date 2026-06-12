---
title: "[SOLVED] Why does machine want to remove all these/"
date: 2008-10-05
forum: General Help
---

### Post by DougieFresh4U on 2008-10-05
I did a 'Orphaned Package' removal and now after I selected remove all and it went through it's process, now when doing update it comes up with wanting to remove all this:
```
dougie@DougiesLeanMachine:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 gcj-4.3-base libstrigiqtdbusclient0 libclucene0ldbl python-zopeinterface
  libgtk2.0-0-dbg gappletviewer-4.3 evolution-data-server-dbg python-twisted-core
  libgsf-gnome-1-114 libqt4-opengl libecj-java rhythmbox-dbg gstreamer0.10-plugins-base-dbg
  fakeroot libatk1.0-dbg python-pexpect libglade2-ruby1.8 libgcj9-0 ttf-wqy-zenhei libgcj-bc
  libgsf-1-114-dbg libgconf2-ruby librdf0 kdebase-runtime-data-common linux-headers-2.6.27-4
  libgda3-common evince-dbg mplayer-skins python-twisted-web python-gamin antlr libpango1.0-0-dbg
  linux-doc-2.6.27 libsvga1 libsp1c2 libgnomedb3-common libgnomedb3-4 libgnomevfs2-0-dbg
  liblog4j1.2-java-gcj python-pycurl kdebase-runtime ttf-kannada-fonts bsh-gcj libregexp-java
  kdelibs5 phonon evolution-dbg libjaxp1.3-java-gcj libkdegames4 libatk1-ruby1.8 mplayer m4
  libatspi-dbg liblog4j1.2-java autoconf python-pyogg libglade2-ruby libgnome2-ruby1.8 ecj-gcj
  libservlet2.4-java libaccess-bridge-java kde-icons-oxygen librasqal0 libxft2-dbg libglide2
  libamrnb3 kdegames-mahjongg-data libggi-target-x libxerces2-java-gcj libfontconfig1-dbg openjade
  gij-4.3 python-pyvorbis intltool python-serial libtool libbcel-java libx264-59 libgoffice-dbg
  libgoffice-0-6-common libsoprano4 python-ogg redland-utils xulrunner-1.9-dom-inspector
  python-pam python-openssl libgnomecanvas2-ruby1.8 libgsf-gnome-1-114-dbg gcj-4.3 firefox-3.0-dev
  libamrwb3 libenca0 ecj bsh kdebase-runtime-bin-kde4 libgda3-sqlite gnome-splashscreen-manager
  kdelibs5-data python-mutagen default-jre gstreamer0.10-plugins-ugly-dbg libggi2 python-cddb
  libfltk1.1 libslab0 libgcj-common gjdoc gstreamer0.10-plugins-good-dbg libgii1 ttf-telugu-fonts
  libjaxp1.3-java openjdk-6-jre-headless bug-buddy libgcj9-dev autotools-dev libgnomedb3-bin
  tzdata-java libgnome2-ruby java-gcj-compat-headless libgconf2-ruby1.8 libxul0d
  libloudmouth1-0-dbg python-pyopenssl openjdk-6-jre libjline-java openjdk-6-jre-lib libgcj9-jar
  libxerces2-java libxml2-dbg libostyle1c2 libglib2-ruby1.8 gnome-panel-dbg libgtk2-gladexml-perl
  java-gcj-compat libltdl7-dev libqt4-svg libgii1-target-x phonon-backend-gstreamer
  libgnomedb3-4-dbg libcairo-ruby1.8 libgoffice-0-6 libstreamanalyzer0 libphonon4 libnss3-1d-dbg
  libxalan2-java firefox-3.0-dom-inspector nautilus-dbg update-motd libgdk-pixbuf2-ruby1.8
  libmozjs0d automake libgtkhtml3.14-dbg java-gcj-compat-dev libgcj9-0-awt kdelibs-bin libgcj9-src
  fastjar rhino jade gnome-applets-dbg liboobs-1-4-dbg khelpcenter4 libgda3-bin ttf-oriya-fonts
  libgda3-3 libnspr4-0d-dbg epiphany-browser-dbg libart2-ruby1.8 libgda3-3-dbg libgtk2-ruby1.8
  libgnome2-gconf-perl libstreams0 libraptor1 libgnomeui-0-dbg python-smartpm docbook-dsssl
  libglib2.0-0-dbg default-jre-headless libxul-common ca-certificates-java libecj-java-gcj
  totem-dbg ttf-bengali-fonts soprano-daemon landscape-common kdebase-runtime-data raptor-utils
  python-gpod libgail-gnome-dbg python-twisted-bin libpango1-ruby1.8 libmx4j-java docbook gimp-dbg
  libxalan2-java-gcj libgstreamer0.10-0-dbg
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dougie@DougiesLeanMachine:~$ 
```
Do I need these packages . When I did orphaned package remove it removed frostwire. Why would frostwire have been an orphaned package? I believe I have done some thing really really bad here

---

### Post by Idefix82 on 2008-10-05
I never remove the orphaned packages by default but look at every single one of them. I also do it only immediately after removing something by hand so that I can clearly see which new packages appeared in the orphaned list. There is a plugin for Synaptic which filters orphaned packages. There you can rightclick on a package and see all its dependencies and dependants. Then you can still decide whether or not you want to keep it.

To answer your question: once you remove an orphaned package, other packages become orphaned. Imagine this scenario: Package A is needed by Package B and by nothing else. If B is removed then A is not needed by anyone any more and appears as orphaned now. However, **you** might need it.

For now I would just reinstall frostwire if you need it. That should considerably shorten your list you just posted since many of these packages will stop being orphaned because they will be needed by frostwire.
If on the other hand you don't need frostwire then go through this long list, have a look at the descriptions and the dependencies of each package and remove it if you really don't need it. I recommend you do that in the Synaptic plugin since you can browse descriptions and dependencies more easily there.

Edit: Here you can find a guide as to how to set up the plugin I was talking about. I would use the rest of the guide with extreme caution since among other things it suggests to do exactly what you did, which can clearly backfire:
[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

