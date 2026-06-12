---
title: "Cannot upgrade from 7.04 to 7.10"
date: 2008-08-04
forum: General Help
---

### Post by porlaizquierda on 2008-08-04
I've posted this before but I still can't get it to upgrade. When I try to upgrade I still get this message.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
 

I don't know why it says that twice. Someone help please.

---

### Post by LowSky on 2008-08-04
```
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by porlaizquierda on 2008-08-06
I did what you said and now my computer won't start. When i turn it on the screen says:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? (yes) (no)

When I clock yes there is a bunch of stuff that could write down if needbe. Then it asks if I want to view teh detailed X server output which is of course way too long to write down. 

After all that it tells me:

The X server is now disabled. Restart GDM when it is configured correctly.

Afterwards it tells me to log in. loginname login:

I log in with my user name and password and then it tells me my last login and and how Ubuntu is free software and it has no warranty and then it just has my login name 

loginname@loginname:~$

I have no idea what to do. What the heck happened to computer?! Help me on this one!

---

### Post by zvacet on 2008-08-06
```
  sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```

```
 sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

---

### Post by porlaizquierda on 2008-08-06
Thanks! I'm now running 7.10. But I only wrote in the first code you gave me. Should I run the other one as well in Terminal. Plus when I try to get updates from Update manager I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Does that have to do with my upgrading or that unrelated? Let me know. Thanks.

---

### Post by tech9 on 2008-08-06
IMHO - I would backup all your data and install 7.10 cleanly. I know it more work, but it will pay off in the long run. I have had nothing but problems when upgrading.

---

### Post by zvacet on 2008-08-06
@ **porlaizquierda**

>  Should I run the other one as well in Terminal.

Yes,because you get message to run 

```
sudo dpkg --configure -a
```

and that was one of commands you should run as I posted to you.Purpose of last three comands is to clean mess if it comes to that.At the end you should have full functional Gutsy runing.

---

### Post by porlaizquierda on 2008-08-06
Ok it seemed to have worked. I put in the configure command first and the the three commands that you gave me earlier. It tells me that I need to use a certain amount of disk space and if I would like to continue. When I type Y it aborts. When I type no it aborts. Should I worry about this? Should I cut my losses and just keep 7.10 and not bother to upgrade to 8.04?

---

### Post by zvacet on 2008-08-07
> It tells me that I need to use a certain amount of disk space and if I would like to continue.

Run command which tells you that and post output here.

---

### Post by porlaizquierda on 2008-08-07
It's something a little different now.

porlaizquierda@porlaizquierda:~$  sudo apt-get update && sudo apt-get dist-upgrade
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Fetched 5B in 11s (0B/s) 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-orca wvdial
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
porlaizquierda@porlaizquierda:~$   sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto gfaim-data liblash2 python-zopeinterface
  libconvert-binhex-perl python-twisted-names imlib11 python-twisted-core
  linphone-common libsoap-lite-perl libode0c2 guile-1.8 scorched3d-data
  libosip2-3 mysql-client libclan2c2a-jpeg lilypond-data libclan2c2a-sound
  libevent-execflow-perl libxml-libxml-common-perl airstrike-common
  libcairo-ruby tetex-base libnet-daemon-perl libgtk1.2 libcrypt-ssleay-perl
  liblockdev1 libkipi0 fgfs-base libatk1-ruby libglib1.2 libnet-ssleay-perl
  libwxgtk2.4-1 sqlite python-twisted-web libxml-namespacesupport-perl
  libexiv2-0.12 libfame-0.9 libclanlib2c2a python-mysqldb liboggflac3
  libmagick++9c2a armagetron-common libintl-perl libzvbi0
  python-twisted-runner libdbi-perl libpvm3 libdbd-mysql-perl libjack0.100.0-0
  boson-data refblas3 libglib2-ruby python-imaging-tk libclan2c2a-vorbis
  libtk-tablematrix-perl libterm-readkey-perl libsuperlu3 libpostproc0d
  python-pyogg libclan2c2a-gui libsqlite0 mysql-client-5.0 libdv-bin
  libpango1-ruby libboost-date-time1.33.1 libogg-dev libarchive-zip-perl
  libossp-uuid-perl libgtk-jni libavformat0d libclan2c2a-png libplrpc-perl
  xmltv-util guile-1.8-libs python-pyvorbis libossp-uuid15 tetex-bin
  python-twisted-mail libcairo-java libpoker-eval
  linux-headers-2.6.20-16-generic gettext python-editobj apg
  libgdk-pixbuf2-ruby blt python-tk libgmp3c2 python-imaging libt1-5
  libevent-rpc-perl ogmtools libio-stringy-perl gtk2-ex-formfactory-perl gpp
  libhtml-tableextract-perl giblib1 libyate1.1.0 libxml-libxml-perl
  python-cerealizer libzvbi-common python-twisted-lore python-twisted-conch
  lsdvd libxml-sax-perl freepats ladspa-sdk vamps python-pyopenssl
  python-twisted-news python-twisted-words libsigc++-1.2-5c2 python-twisted
  transcode libglib-java python-soya libzipios++0c2a docker libdate-manip-perl
  libhttp-cache-transparent-perl anyevent-perl libwww-mechanize-perl
  python-tofu libqt3-mt-sqlite linphone-nox libfluidsynth1 yate
  linux-headers-2.6.20-16 libmime-perl xawtv-plugins libmime-lite-perl
  libgtk1.2-common imlib-base libfcgi-perl libxml-writer-perl liblo0
  python-poker-engine libevent-perl bwidget qobex liblinphone1 libavcodec0d
  libmediastreamer0 mpg321 libboost-filesystem1.33.1 libclan2c2a-mikmod
  libgpgme11 libraptor1 libpri1.2 dbconfig-common supertux-data-stable
  libio-socket-ssl-perl libxul-common simgear0 libswt3.2-gtk-jni libquicktime0
  ladcca2 libcal3d11c2a python-pypoker-eval enigma-data plib1.8.4c2 libwv2-1c2
  libgtkglext1 libvorbis-dev libxerces27 libboost-python1.33.1
  python-twisted-bin libxmltv-perl libortp5 libopenobex1 libgts-0.7-5 texinfo
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
porlaizquierda@porlaizquierda:~$   sudo dpkg --configure -a

---

