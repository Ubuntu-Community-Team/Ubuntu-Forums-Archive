---
title: "How do I uninstall edubuntu to get back to ubuntu?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Compuglobalhypermeganet on 2009-05-20
I am completely new to Linux and I am not sure how I switched from ubuntu to edubuntu, but I do not like edubuntu.  How do I get back to ubuntu?
Thank You in advance to any advice.

---

### Post by xavierp94 on 2009-05-20
> **Compuglobalhypermeganet said:**
> I am completely new to Linux and I am not sure how I switched from ubuntu to edubuntu, but I do not like edubuntu.  How do I get back to ubuntu?
Thank You in advance to any advice.
What method did you use to install Edubuntu in the first place?

---

### Post by Compuglobalhypermeganet on 2009-05-21
> **xavierp94 said:**
> What method did you use to install Edubuntu in the first place?

I have no idea.  The original message said Ubuntu, but after I played around with Ubuntu for several hours the starting message now says Edubuntu.

---

### Post by pyromaniac77 on 2011-03-07
I have this issue also.
I beleive I got Edubuntu through Applications>Ubuntu software center and then downloaded some sort of education pack...

---

### Post by Dutch70 on 2011-03-08
> I have this issue also.
I beleive I got Edubuntu through Applications>Ubuntu software center and then downloaded some sort of education pack...

pyromaniac77, welcome to UF. 
this thread is nearly 2 years old, to get help, you really need to start your own thread.

If you installed it from software center, go back to software center to remove it.

> **Compuglobalhypermeganet said:**
> I am completely new to Linux and I am not sure how I switched from ubuntu to edubuntu, but I do not like edubuntu.  How do I get back to ubuntu?
Thank You in advance to any advice.

If you installed "edubuntu-desktop" from synaptic, then run this command. 

```
sudo apt-get remove atomix atomix-data avogadro-data blinken blt breathe-icon-theme desktop-profiles dia-common dia-gnome dia-libs docbook-xsl docbook-xsl-doc-html edubuntu-artwork edubuntu-desktop edubuntu-docs edubuntu-menueditor gcompris gcompris-data gcompris-sound-en gimp gimp-data gnome-icon-theme-gartoon gobby gsfonts-x11 hal hal-info human-icon-theme human-theme icoutils imagemagick inkscape italc-client kalgebra kalzium kalzium-data kanagram kbruch kdebase-runtime kdebase-runtime-data kdeedu-kvtml-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools khangman khelpcenter4 kig kmplot kolourpaint4 krosspython kstars kstars-data ktouch ktuberling kturtle kubuntu-debug-installer kwordquiz libattica0 libaudio2 libavogadro1 libbabl-0.0-0 libblas3gf libboost-python1.42.0 libcdt4 libcfitsio3 libcln6 libclucene0ldbl libdbusmenu-qt2 libdirectfb-1.2-9 libfli1 libgegl-0.0-0 libgfortran3 libgif4 libgimp2.0 libglew1.5 libgnet2.0-0 libgps19 libgraph4 libgvc5 libhal-storage1 libhal1 libilmbase6 libindi0 libiodbc2 libitalc libkatepartinterfaces4 libkde3support4 libkdecore5 libkdeedu4 libkdegames5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkfile4 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4 libkrossui4 libktexteditor4 libkunitconversion4 libkutils4 liblapack3gf libmagick++3 libmagickcore3-extra libmarblewidget10 libmikmod2 libmng1 libmodplug1 libmpcdec6 libmysqlclient16 libnepomuk4 libnepomukquery4a libnet6-1.3-0 libnetpbm10 libnova-0.12-2 libobby-0.4-1 libopenbabel3 libopenexr6 libpathplan4 libphonon4 libplasma3 libpolkit-qt-1-0 libqalculate5 libqapt-runtime libqapt1 libqca2 libqimageblitz4 libqt3-mt libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4 libreadline5 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-pango1 libsdl-ttf2.0-0 libsmpeg0 libsolid4 libsoprano4 libsqlite0 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libts-0.0-0 libvirtodbc0 libwmf-bin libxcb-shape0 libxcb-xv0 libxdot4 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml++2.6-2 liferea liferea-data marble marble-data marble-plugins mysql-common nanny netpbm odbcinst odbcinst1debian2 oxygen-icon-theme parley parley-data perlmagick pessulus phonon phonon-backend-xine plasma-scriptengine-javascript python-avogadro python-bugbuddy python-gtop python-hachoir-regex python-ldap python-lxml python-numpy python-pysqlite2 python-qt4 python-renderpm python-reportlab python-reportlab-accel python-sip python-sqlite python-tk python-uniconvertor qapt-batch qcad qcad-data qcad-doc qt3-assistant qt3-doc ri-li ri-li-data sabayon scribus shared-desktop-ontologies smartdimmer soprano-daemon step tcl8.5 tk8.5 tsconf ttf-bengali-fonts ttf-dejavu ttf-dejavu-extra ttf-devanagari-fonts ttf-dustin ttf-gujarati-fonts ttf-kannada-fonts ttf-oriya-fonts ttf-sil-andika ttf-sil-doulos ttf-sjfonts ttf-tamil-fonts ttf-telugu-fonts tuxmath tuxpaint tuxpaint-data tuxpaint-plugins-default tuxpaint-stamps-default tuxtype tuxtype-data ubuntu-edu-preschool ubuntu-edu-primary ubuntu-edu-secondary ubuntu-edu-tertiary virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common vym xaos xplanet xplanet-images xserver-xephyr && sudo apt-get install ubuntu-desktop
```

It could remove some things you've recently installed as well. Just reinstall them if so & you should still have all your settings in place.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

