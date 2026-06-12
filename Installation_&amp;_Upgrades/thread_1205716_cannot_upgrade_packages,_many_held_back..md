---
title: "cannot upgrade packages, many held back."
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by washakie on 2009-07-06
Hello,

I have been having problems upgrading. I now have 122 packages being held back, mostly python which I rely heavily on being up to date. I have tried apt-get upgrade and apt-get dist-upgrade after updating of course... My system is running Jaunty:

wash@kie:~$ uname -a
Linux kie 2.6.30-020630rc2-generic #020630rc2 SMP Wed Apr 15 14:00:27 UTC 2009 i686 GNU/Linux
wash@kie:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  aria2 asymptote banshee basket cairo-dock cairo-dock-data calibre calibre-bin conduit furiusisomount gfortran-4.3 gftp gftp-text glade gnome-do gnome-do-plugins
  gnome-netstatus-applet gpicview grass gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gufw imgseek ipython kbib kile libboost-regex1.34.1 libcegui-mk2-1 libcegui-mk2-dev
  libcryptgps-ocaml-dev libfreebob0 libgdal1-1.5.0 libgeos-c1 libhdf5-serial-1.6.6-0 liblablgtk2-gnome-ocaml liblablgtk2-gnome-ocaml-dev liblablgtk2-ocaml liblablgtk2-ocaml-dev
  libmapnik0.5 libnetcdf4 libnethttpd-ocaml-dev libocamlnet-ocaml libocamlnet-ocaml-dev liborange0 libpcre-ocaml libpcre-ocaml-dev libqt4-core libsqliteodbc libvtk5-dev
  libwww-curl-perl libxerces-c2-dev libxerces-c28 libxml-light-ocaml-dev libyaz3 lilypond lilypond-data luatex lyx lyx-common mayavi2 meld merkaartor pdftk perl-tk
  phonon-backend-gstreamer photo-uploader pybackpack pylint python-beautifulsoup python-cherrypy python-django python-feedparser python-gps python-insighttoolkit3
  python-logilab-astng python-logilab-common python-mapnik python-mapscript python-matplotlib python-matplotlib-dbg python-opengl python-openid python-paste python-pdftools
  python-pychart python-pyexiv2 python-pygraphviz python-pyparsing python-pypdf python-pysqlite2 python-pythonmagick python-qt3-gl python-scgi python-vtk python-webkit
  python-webkit-dev python-webkitgtk python-webkitgtk-dev python-yapgvb qtractor r-cran-rgtk2 rasmol rdiff-backup rednotebook screen-profiles screenlets seahorse-plugins
  synce-trayicon tangogps texlive-metapost texlive-xetex texmaker totem-gstreamer unetbootin viking vim-gtk vlc vlc-nox vtk-tcl wireshark wireshark-common yakuake
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.

Any thoughts on why the upgrades are being held back??

Thanks!

---

### Post by wojox on 2009-07-06
Try

```
sudo apt-get update
```

Then

```
sudo apt-get upgrade
```

---

### Post by washakie on 2009-07-06
Yes, I have tried the following:

sudo apt-get update
sudo apt-get upgrade
sudo aptitude update
sudo aptitude upgrade

#then, in desperation:
sudo apt-get dist-upgrade
sudo aptitude dist-upgrade

Nothing seems to help. I expect it must be a dependency problem, but I don't know where to begin determining which of the 122 packages may be the root of the problem.

---

### Post by wojox on 2009-07-06
Ok try this

```
apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
```

It should tell you what's keeping or removing a package you may use.

---

### Post by taurus on 2009-07-06
Or post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by washakie on 2009-07-06
It's a mess! I'm not sure what is going on. Here's the output:

Reading package lists... Done                                                                                        
Building dependency tree                                                                                             
Reading state information... Done                                                                                    
Calculating upgrade... Starting                                                                                      
Starting 2                                                                                                           
Investigating phonon-backend-gstreamer                                                                               
Package phonon-backend-gstreamer has broken dep on libqt4-opengl                                                     
Investigating libxerces-c28                                                                                          
Package libxerces-c28 has broken dep on libicu40                                                                     
Investigating libgdal1-1.5.0                                                                                         
Package libgdal1-1.5.0 has broken dep on libsqlite3-0                                                                
Investigating libnetcdf4                                                                                             
Package libnetcdf4 has broken dep on libstdc++6                                                                      
Investigating libgeos-c1                                                                                             
Package libgeos-c1 has broken dep on libstdc++6                                                                      
Investigating libhdf5-serial-
[snip...]


 Try to Re-Instate photo-uploader                                                                                    
 Try to Re-Instate grass

---

### Post by washakie on 2009-07-06
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                     
# newer versions of the distribution.                                                         

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty universe                   
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-updates universe           

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty multiverse                  
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse          

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner                   
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner               

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe                                                              
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe                                                          
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse                                                            
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse                                                        

## Bibus
# deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
# deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

# deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

# deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) experimental main
# deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

## Numpy / scipy
# deb [http://debs.astraw.com/](http://debs.astraw.com/) dapper/

# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid MAIN

## Python(x,y)
deb [http://linux.pythonxy.com/ubuntu](http://linux.pythonxy.com/ubuntu) intrepid universe
deb-src [http://linux.pythonxy.com/ubuntu](http://linux.pythonxy.com/ubuntu) intrepid universe
deb [http://apt.paulnovo.org/ubuntu](http://apt.paulnovo.org/ubuntu) intrepid main
deb-src [http://apt.paulnovo.org/ubuntu](http://apt.paulnovo.org/ubuntu) intrepid main


deb [http://ppa.launchpad.net/gael-varoquaux/ppa/ubuntu](http://ppa.launchpad.net/gael-varoquaux/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gael-varoquaux/ppa/ubuntu](http://ppa.launchpad.net/gael-varoquaux/ppa/ubuntu) hardy main

## xorg-edgers

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main #xorg-edgers PPA
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main #xorg-edgers PPA

# Papparazzi UAV software
deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) jaunty main

deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main

#back in time
deb [http://backintime.le-web.org/repository](http://backintime.le-web.org/repository) stable main

# synce
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main

---

### Post by washakie on 2009-07-06
It seems it may be related to python-support. How can I upgrade this package?

wash@kie:/opt$ sudo apt-get install python-matplotlib
Reading package lists... Done                
Building dependency tree                     
Reading state information... Done            
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.                                    
The following information may help to resolve the situation:      

The following packages have unmet dependencies:
  python-matplotlib: Depends: python-support (>= 0.90.0) but 0.8.7ubuntu4 is to be installed

---

### Post by taurus on 2009-07-06
Serious, you are asking for big trouble there because you have four different releases, hardy, intrepid, jauntry, and karmic, in /etc/apt/sources.list!  What's up with that?

---

### Post by Ra-Hoor-Khuit on 2009-07-06
Why do you have repos for both Intrepid *and* Jaunty enabled?

---

### Post by taurus on 2009-07-06
> **washakie said:**
> It seems it may be related to python-support. How can I upgrade this package?

wash@kie:/opt$ sudo apt-get install python-matplotlib
Reading package lists... Done                
Building dependency tree                     
Reading state information... Done            
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.                                    
The following information may help to resolve the situation:      

The following packages have unmet dependencies:
  python-matplotlib: Depends: python-support (>= 0.90.0) but 0.8.7ubuntu4 is to be installed

You have to decide which release you want to use and stick with that version only.  Mixing releases will only cause trouble and trouble is all you will get.

---

### Post by washakie on 2009-07-06
Dunno,guess it was left over from something???

Can I just have karmic everywhere? Because I seem to need it for python packages I run...

---

### Post by taurus on 2009-07-06
You can edit /etc/apt/sources.list and change everything to karmic.  Then, see if it works now when you try to upgrade it.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by aspergerian on 2009-10-31
According to other threads, Bibus on Hardy seems to require 1.4.2, which does not seem offered at [http://sourceforge.net/projects/bibus-biblio/files/bibus-biblio/bibus-1.4.2/](http://sourceforge.net/projects/bibus-biblio/files/bibus-biblio/bibus-1.4.2/)


#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

---

