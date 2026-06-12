---
title: "can't dist-upgrade"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Drone4four on 2009-05-02
edit: This thread was first created when I was trying to upgrade to Jaunty.  After troubleshooting Jaunty was upgraded just fine in May but now I am trying to upgrade to Karmic from Jaunty and I am running into some errors.  Skip down to post #6 for the error message I get from the Karmic upgrade

I'm on Ibex and the dist-upgrade command doesn't work.  Here is my input and output for that command:```
daniel@ibex:~$ sudo aptitude update && sudo aptitude upgrade && sudo aptitude di
st-upgrade && sudo aptitude autoclean >>distupgrade
0% [Working]^C
daniel@ibex:~$ sudo aptitude update && sudo aptitude upgrade && sudo aptitude di
st-upgrade && sudo aptitude autoclean >>distupgrade3
Ign http://www.phoronix-test-suite.com pts.debian/ Release.gpg
Ign http://www.phoronix-test-suite.com pts.debian/ Translation-en_US            
Ign http://www.phoronix-test-suite.com pts.debian/ Release                      
Get:1 http://security.ubuntu.com intrepid-security Release.gpg [189B]           
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US         
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US   
Get:2 http://archive.canonical.com intrepid Release.gpg [189B]                  
Ign http://archive.canonical.com intrepid/partner Translation-en_US             
Ign http://www.phoronix-test-suite.com pts.debian/ Packages                     
Get:3 http://us.archive.ubuntu.com intrepid Release.gpg [189B]                  
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US     
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US   
Hit http://security.ubuntu.com intrepid-security Release                        
Hit http://www.phoronix-test-suite.com pts.debian/ Packages                     
Hit http://archive.canonical.com intrepid Release                               
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US       
Get:4 http://us.archive.ubuntu.com intrepid-updates Release.gpg [189B]       
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US     
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security/main Packages                  
Ign http://archive.canonical.com intrepid/partner Packages                      
Hit http://us.archive.ubuntu.com intrepid Release                            
Hit http://security.ubuntu.com intrepid-security/restricted Packages            
Hit http://security.ubuntu.com intrepid-security/main Sources                   
Hit http://security.ubuntu.com intrepid-security/restricted Sources          
Hit http://security.ubuntu.com intrepid-security/universe Packages              
Hit http://us.archive.ubuntu.com intrepid-updates Release                       
Hit http://archive.canonical.com intrepid/partner Packages                      
Hit http://security.ubuntu.com intrepid-security/universe Sources               
Hit http://security.ubuntu.com intrepid-security/multiverse Packages         
Hit http://security.ubuntu.com intrepid-security/multiverse Sources          
Hit http://us.archive.ubuntu.com intrepid/main Packages                      
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources 
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Get:5 http://cafelinux.org tinwoodman Release.gpg [189B]
Ign http://cafelinux.org tinwoodman/main Translation-en_US
Hit http://cafelinux.org tinwoodman Release       
Ign http://cafelinux.org tinwoodman/main Packages
Hit http://cafelinux.org tinwoodman/main Packages
Fetched 945B in 5s (166B/s)
Reading package lists... Done

[COLOR="Red"]W: The "upgrade" command is deprecated; use "safe-upgrade" instead.[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or 0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

[COLOR="Red"]daniel@ibex:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade[/COLOR]
removed.

```

How do I upgrade to Jaunty?> 

---

### Post by taurus on 2009-05-02
You should consider editing /etc/apt/sources.list and comment out those 3rd party repos first before you attend to upgrade to Jaunty.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by snowpine on 2009-05-02
dist-upgrade is used to upgrade within the same release (in your case Intrepid) when a new kernel version or core library is available. 

To upgrade to Jaunty,

sudo update-manager -d

The update manager should automatically comment out all of your 3rd party repos.

Good luck!

---

### Post by Drone4four on 2009-05-02
sudo update-manager -d did the trick.  Thanks snowpine.  What happened to the gratitude function?  I can't thank you.

---

### Post by snowpine on 2009-05-03
Then I can't say you're welcome. :)
Glad it worked, enjoy Jaunty!

---

### Post by Drone4four on 2009-10-29
Now I'm trying to upgrade to Karmic Koala from Jaunty.  Here is the update-manager command and its output```
daniel@ibex:~$ sudo update-manager -d
[sudo] password for daniel: 
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
No candidate ver:  libvalerie0.2.5
No candidate ver:  libisc44
No candidate ver:  linux-image-2.6.27-9-generic
No candidate ver:  libxfce4mcs-client3
No candidate ver:  libx264-59
No candidate ver:  linux-restricted-modules-2.6.27-11-generic
No candidate ver:  kdeplasma-addons-libs4
No candidate ver:  libnm-util0
No candidate ver:  linux-restricted-modules-2.6.27-9-generic
No candidate ver:  belocs-locales-bin
No candidate ver:  libxcb-xlib0
No candidate ver:  libpulsecore5
No candidate ver:  libmlt++0.2.5
No candidate ver:  libparted1.8-9
No candidate ver:  libmlt0.2.5
No candidate ver:  libavcodec51
No candidate ver:  gtk-engines-xenophilia
No candidate ver:  libplasma2
No candidate ver:  libmagick10
No candidate ver:  libarts1c2a
No candidate ver:  libgnome-desktop-2-7
No candidate ver:  libmjpegtools0c2a
No candidate ver:  libdvdread3
No candidate ver:  libntfs-3g28
No candidate ver:  libexiv2-4
No candidate ver:  libgpod3
No candidate ver:  ktnef
No candidate ver:  libmiracle0.2.5
No candidate ver:  libxfce4mcs-manager3
No candidate ver:  libkdegames4
No candidate ver:  xfce4-mcs-manager
No candidate ver:  libartsc0
No candidate ver:  linux-image-2.6.27-11-generic
No candidate ver:  libkipi5
No candidate ver:  libopal-2.2
No candidate ver:  libpoppler3
No candidate ver:  libpoppler-glib3
No candidate ver:  libdns43
No candidate ver:  librasqal0
No candidate ver:  libvalerie0.2.5
No candidate ver:  libisc44
No candidate ver:  linux-image-2.6.27-9-generic
No candidate ver:  libx264-59
No candidate ver:  libnm-util0
No candidate ver:  linux-restricted-modules-2.6.27-9-generic
No candidate ver:  ktnef
No candidate ver:  belocs-locales-bin
No candidate ver:  libxcb-xlib0
No candidate ver:  libpulsecore5
No candidate ver:  libxfce4mcs-client3
No candidate ver:  libmlt++0.2.5
No candidate ver:  libparted1.8-9
No candidate ver:  libsox1
No candidate ver:  gdk-imlib11
No candidate ver:  libmlt0.2.5
No candidate ver:  libavcodec51
No candidate ver:  gtk-engines-xenophilia
No candidate ver:  libplasma2
No candidate ver:  linux-restricted-modules-2.6.27-11-generic
No candidate ver:  libmagick10
No candidate ver:  imlib-base
No candidate ver:  libarts1c2a
No candidate ver:  libgnome-desktop-2-7
No candidate ver:  libmjpegtools0c2a
No candidate ver:  libdvdread3
No candidate ver:  libntfs-3g28
No candidate ver:  kdeplasma-addons-libs4
No candidate ver:  libexiv2-4
No candidate ver:  libgpod3
No candidate ver:  libmiracle0.2.5
No candidate ver:  libgdk-pixbuf2
No candidate ver:  libxfce4mcs-manager3
No candidate ver:  libkdegames4
No candidate ver:  xfce4-mcs-manager
No candidate ver:  libartsc0
No candidate ver:  linux-image-2.6.27-11-generic
No candidate ver:  libkipi5
No candidate ver:  libopal-2.2
No candidate ver:  libpoppler3
No candidate ver:  libpoppler-glib3
No candidate ver:  libdns43
No candidate ver:  librasqal0
daniel@ibex:~$ 

```
Here is the error message that pops up titled 'karmic':```
Could not download the upgrades

The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.



Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kalzium_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kamera_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kdeedu-kvtml-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kanagram_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kapman_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/katomic_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kbattleship_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kblackbox_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kbounce_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kbruch_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kcalc_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kcharselect_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kcron_4.3.2-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kde-icons-mono_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.1.12+git20090826-0ubuntu8_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit/libpolkit2_0.9-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit/libpolkit-dbus2_0.9-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit/libpolkit-grant2_0.9-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/polkit-qt/libpolkit-qt0_0.9.2+svn966498-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebindings/python-kde4_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4-dbus_4.6-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kdeutils/kde-printer-applet_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/printer-applet_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kde-style-bespin/kde-style-bespin_0.1~svn090802-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kde-style-bespin/kde4-style-bespin_0.1~svn090802-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmag_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmouth_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmousetool_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kdeaccessibility_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/ksystemlog_4.3.2-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kuser_4.3.2-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kdeadmin_4.3.2-0ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kdeartwork-emoticons_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kdeartwork-style_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10.dfsg.1-2ubuntu7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/plasma-widgets-workspace_4.3.2-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-bin_4.3.2-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-data_4.3.2-0ubuntu7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit/policykit_0.9-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kscreensaver_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/plasma-desktopthemes-artwork_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kdeartwork_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-plasma_4.3.2-0ubuntu3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/plasma-widget-folderview_4.3.2-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/klipper_4.3.2-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/ksysguard_4.3.2-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/systemsettings_4.3.2-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace_4.3.2-0ubuntu7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kgeography-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kgeography_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/khangman_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-python1.38.0_1.38.0-6ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kig_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/klettres-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/klettres_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kmplot_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cfitsio3/libcfitsio3_3.140-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libf/libfli1/libfli1_1.7-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libindi/libindi0_0.6-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kstars-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kstars_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/ktouch_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kturtle_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kwordquiz_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/parley-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/parley_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cln/libcln5_1.2.2-2ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libq/libqalculate/libqalculate4_0.9.6-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/step_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kdeedu_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/bovo_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kdiamond_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kgoldrunner_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kiriki_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/killbots_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ktron_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kjumpingcube_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/klines_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kdegames-mahjongg-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kmahjongg_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kmines_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/knetwalk_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kolf_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kollision_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/konquest_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kdegames-card-data_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kpat_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kreversi_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ksame_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kshisen_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kspaceduel_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ksudoku_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ksquares_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ktuberling_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kfourinline_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/lskat_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kubrick_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kblocks_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kbreakout_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qca2/libqca2_2.0.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ksirk_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kdesnake_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kdegames_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kcolorchooser_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kgamma_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kolourpaint4_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kruler_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libksane0_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/ksnapshot_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/ebook-tools/libepub0_0.1.1-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libokularcore1_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-qt4-3_0.12.0-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/okular_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kdegraphics_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdelirc_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kio-plugins_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/libkcddb4_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kmix_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kscd_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kget_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/libkopete4_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmsn/libmsn0.1_4.0~beta6-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kppp_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krdc_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krfb_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork_4.3.2-0ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-filesharing_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-strigi-plugins_4.3.2-0ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim_4.3.2-0ubuntu6_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdessh_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdetoys/kteatime_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdetoys/ktux_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdetoys/kweather_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdetoys/kdetoys_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdf_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kfloppy_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kgpg_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ktimer_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kwalletmanager_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/okteta_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/plasma-scriptengine-superkaramba_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/sweeper_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdeutils_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_4.3.2-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/khelpcenter4_4.3.2-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg-progs_6b-14build1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/konq-plugins/konq-plugins_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror-nsplugins_4.3.2-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-data_5.08-0ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kscreensaver-xsavers_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/ksysguardd_4.3.2-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kde-style-bespin/kwin-style-bespin_0.1~svn090802-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-style-qtcurve/kwin-style-qtcurve_0.69.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kde-style-bespin/kwin4-style-bespin_0.1~svn090802-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/lame_3.98.2+debian-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.4.18_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.4.18_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scowl/wamerican_6-3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scowl/wbritish_6-3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/stlport4.6/libstlport4.6ldbl_4.6.2-5build1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ure_1.5.1+OOo3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/uno-libs3_1.5.1+OOo3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcolamd2.7.1_3.4.0-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lp-solve/lp-solve_5.5.0.13-6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-common_3.1.1-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-en-za_3.1.1-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-en-gb_3.1.1-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_3.1.1-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.1.1-5ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-galaxy_3.1.1-5ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.1.1-5ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.1.1-5ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hyphen/libhyphen0_2.4-4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27-gnutls_0.28.6-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hyphen/openoffice.org-hyphenation-en-us_2.4-4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-support-writing-en/language-support-writing-en_9.10+20090909_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-support-en/language-support-en_9.10+20090909_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/launchpad-integration_0.1.26_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_3.7.15-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libao/libao2_0.8.8-5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.3.8-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-plugins/libasound2-plugins_1.0.20-1ubuntu8_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/liba/libast/libast2_0.7-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/atk1.0/libatk1.0-data_1.28.0-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.25-1ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-gobject0_0.6.25-1ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-ui0_0.6.25-1ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/b/boost/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/b/boost/libboost-python1.34.1_1.34.1-16ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/b/boost/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo-perl/libcairo-perl_1.061-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcanberra/libcanberra-gtk-module_0.15-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libc/libcompress-raw-bzip2-perl/libcompress-raw-bzip2-perl_2.020-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libi/libio-compress-perl/libcompress-zlib-perl_2.020-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libi/libio-compress-perl/libio-compress-zlib-perl_2.020-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libi/libio-compress-perl/libio-compress-base-perl_2.020-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libi/libio-compress-perl/libio-compress-perl_2.020-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcompress-raw-zlib-perl/libcompress-raw-zlib-perl_2.020-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/seahorse/libcryptui0_2.28.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2020-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/libdbi-perl_1.609-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.011-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/eina/libeina-svn-03_0.0.2.062-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/eet/libeet1_1.2.2-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libe/libevent/libevent-1.4-2_1.4.11-stable-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libf/libfreezethaw-perl/libfreezethaw-perl_0.45-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/libgcj-bc_4.4.1-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gcj-4.3/libgcj9-0_4.3.4-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gcj-4.3/libgcj9-jar_4.3.4-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgdata/libgdata-common_0.4.0-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgdata/libgdata5_0.4.0-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/glew/libglew1.5_1.5.1-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libglib-perl/libglib-perl_1.221-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gmyth/libgmyth0_0.7.1-1.1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-bluetooth/libgnome-bluetooth7_2.28.1-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpango-perl/libpango-perl_1.220-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgtk2-perl/libgtk2-perl_1.221-4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome2-canvas-perl/libgnome2-canvas-perl_1.002-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome2-vfs-perl/libgnome2-vfs-perl_1.081-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome2-perl/libgnome2-perl_1.042-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-vfs/libgnomevfs2-bin_2.24.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs/libgnomevfs2-extra_2.24.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/goocanvas/libgoocanvas3_0.15-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/goocanvas/libgoocanvas-common_0.15-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod4_0.7.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod-common_0.7.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk-vnc/libgtk-vnc-1.0-0_0.3.9-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libindicate/libindicate-gtk1_0.2.3-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-tools/libiw29_29-2ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/j/jakarta-log4j/liblog4j1.2-java-gcj_1.2.15-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libl/liblrdf/liblrdf0_0.4.0-1.2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.1.1+debian-1build1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools-1.9_1.9.0-0.5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-cairo1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-posix1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip0.84-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-data1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-data2.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-getoptions1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-getoptions2.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-i18n-west1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-i18n-west2.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-i18n1.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mono/libmono-i18n2.0-cil_2.4.2.3+dfsg-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_2.4.2.3+dfsg-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27_0.28.6-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util1_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libn/libnotify/libnotify-bin_0.4.5-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nss-mdns/libnss-mdns_0.10-3ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1-gnome/libpolkit-gtk-1-0_0.94-1+1git.230873_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.28.1-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-tools-backends/system-tools-backends_2.8.2-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libo/liboobs/liboobs-1-4_2.22.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libpam-ck-connector_0.3.1-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_2.28.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcsc-lite/libpcsclite1_1.5.3-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.3.1-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pwlib/libpt-1.10.10-plugins-alsa_1.10.10-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pwlib/libpt-1.10.10-plugins-v4l_1.10.10-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pwlib/libpt-1.10.10-plugins-v4l2_1.10.10-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pwlib/libpt-1.10.10_1.10.10-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-browse0_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.6.2-1ubuntu7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qca2-plugin-ossl/libqca2-plugin-ossl_0.1~20070904-4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qzion/libqzion0_0.4.0-0ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qedje/libqedje0_0.4.0-0ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim/libscim8c2a_1.4.9-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libsmi/libsmi2-common_0.4.8+dfsg-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libsmi/libsmi2ldbl_0.4.8+dfsg-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.6.5dfsg-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.6.5dfsg-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/swt-gtk/libswt-cairo-gtk-3.4-jni_3.4.2-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/swt-gtk/libswt-gnome-gtk-3.4-jni_3.4.2-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/swt-gtk/libswt-mozilla-gtk-3.4-jni_3.4.2-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-glib/libtelepathy-glib0_0.9.0-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar/thunar_1.0.1-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar/libthunar-vfs-1-2_1.0.1-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar/thunar-data_1.0.1-1ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_2.2.6a-4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-2ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-xcb1_1.2.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libx/libxfce4menu/libxfce4menu-0.1-0_4.6.1-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-sax-perl/libxml-sax-perl_0.96+dfsg-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-simple-perl/libxml-simple-perl_2.18-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-twig-perl/libxml-twig-perl_3.32-3ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xplc/libxplc0.3.13_0.3.13-2ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.24_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.14.27_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.14.27_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/makepasswd/makepasswd_1.10-4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mdetect/mdetect_0.5.2.3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/media-player-info/media-player-info_3-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/min12xxw/min12xxw_0.0.9-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/mjpegtools_1.9.0-0.5ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091014t233208.16f3e00-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mousetweaks/mousetweaks_2.28.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mtools/mtools_4.0.10-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/murrine-themes/murrine-themes_0.90.2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/mysql-client-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-sendto/nautilus-sendto_2.28.0-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.6.9-3ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-common_0.90_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20091009-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/notify-osd-icons/notify-osd-icons_0.3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-173/nvidia-173-modaliases_173.14.20-0ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-180/nvidia-185-modaliases_185.18.36-0ubuntu9_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvidia-graphics-drivers-180/nvidia-180-modaliases_185.18.36-0ubuntu9_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-96/nvidia-96-modaliases_96.43.13-0ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-common/nvidia-common_0.2.15_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/onboard/onboard_0.92.0-0ubuntu3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-en-gb_3.1.1-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-en-us_3.1.1-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db/openprinting-ppds_20090825-0ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.6.1-3ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/orage/orage_4.6.1-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/os-prober/os-prober_1.35_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.10.dfsg.1-2ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin-libnotify/pidgin-libnotify_0.14-1ubuntu11_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-otr/pidgin-otr_3.2.0-4ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pygoocanvas/python-pygoocanvas_0.14.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pitivi/pitivi_0.13.3-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pnm2ppa/pnm2ppa_1.12-16.2ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-udev_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-esound-compat_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_0.9.19-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pxljr/pxljr_1.1-0ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libb/libbeagle/python-beagle_0.3.9-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-dateutil/python-dateutil_1.4.1-3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/f/feedparser/python-feedparser_4.1-14_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sqlalchemy/python-sqlalchemy_0.5.5-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pyusb/python-usb_0.4.1-5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3.1/python3.1-minimal_3.1.1-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3.1/python3.1_3.1.1-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3-defaults/python3_3.1-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3-defaults/python3-minimal_3.1-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.19-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.6.0-2ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/redland/redland-utils_1.0.9-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/reiserfsprogs/reiserfsprogs_3.6.21-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.5-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/r/rss-glx/rss-glx_0.9.0-2ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/sane-utils_1.0.20-4ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim/scim_1.4.9-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim/scim-gtk2-immodule_1.4.9-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim/scim-modules-socket_1.4.9-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim-bridge/scim-bridge-agent_0.4.16-2ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim-bridge/scim-bridge-client-gtk_0.4.16-2ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/screen-resolution-extra/screen-resolution-extra_0.11_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/seahorse/seahorse_2.28.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/seahorse-plugins/seahorse-plugins_2.28.1-0ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sg3-utils/sg3-utils_1.27-0.1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/splix/splix_2.0.0-2ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sqlite/sqlite_2.8.17-6build1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sqlite3/sqlite3_3.6.16-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_5.1p1-6ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.12-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kdeutils/superkaramba_4.3.2-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.1.12+git20090826-0ubuntu8_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/system-config-printer-kde_4.3.2-0ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tangerine-icon-theme/tangerine-icon-theme_0.27_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tango-icon-theme/tango-icon-theme_0.8.90-3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.19-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/tcltk-defaults/tcl_8.4.16-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar-volman/thunar-volman_0.3.80-2ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.19-3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/toshset/toshset_1.75-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-plugins_2.28.1-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-gstreamer_2.28.1-0ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.28.1-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_2.28.1-0ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.28.1-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-gtk_1.75-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-common_1.75-0ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/tsclient/tsclient_0.150-2ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-core_2.29-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.29-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.29-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-kochi/ttf-kochi-gothic_20030809-3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-kochi/ttf-kochi-mincho_20030809-3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-liberation/ttf-liberation_1.05.1.20090721-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/thaifonts-scalable/ttf-thai-tlwg_0.4.13-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/twolame/twolame_0.3.12-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.8-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/u/ubuntu-gdm-themes/ubuntu-gdm-themes_0.33_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sounds/ubuntu-sounds_0.12_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_0.30_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.9.3-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-motd/update-motd_3.5-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier_0.90_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator_0.2.12_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-common_0.2.12_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-gtk_0.2.12_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.27_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vinagre/vinagre_2.28.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.28.1-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose_3.0.8-dfsg-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/a/azureus/vuze_4.2.0.8-3ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-tools/wireless-tools_29-2ubuntu6_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/c-ares/libc-ares2_1.6.0-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/wireshark_1.2.2-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/wireshark-common_1.2.2-2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-gl/x11proto-gl-dev_1.4.10-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xchat/xchat_2.8.6-4ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xchat/xchat-common_2.8.6-4ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xdg-user-dirs/xdg-user-dirs_0.11-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-settings/xfce4-settings_4.6.3-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfdesktop4/xfdesktop4_4.6.1-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfdesktop4/xfdesktop4-data_4.6.1-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xterm/xterm_243-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-terminal/xfce4-terminal_0.4.2-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-utils/xfce4-utils_4.6.1-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-session/xfce4-session_4.6.1-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-mixer/xfce4-mixer_4.6.1-2ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-appfinder/xfce4-appfinder_4.6.1-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4/xfce4_4.6.1.1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-volumed/xfce4-volumed_0.1.4-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-100dpi/xfonts-100dpi_1.0.0-4build1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-75dpi/xfonts-75dpi_1.0.0-4build1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-base/xfonts-base_1.0.0-6_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-scalable/xfonts-scalable_1.0.0-7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-terminus/xfonts-terminus_4.28-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfprint4/xfprint4_4.6.1-1ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfwm4-themes/xfwm4-themes_4.6.0-2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xinput/xinput_1.4.2-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibmesa-gl-dev_7.4+3ubuntu7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-docs/xorg-docs-core_1.4-5_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.4+3ubuntu7_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-dev_1.6.4-2ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg-dev_7.4+3ubuntu7_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xsane/xsane_0.996-2ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xsane/xsane-common_0.996-2ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-gl_5.08-0ubuntu5_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/oss-compat/oss-compat_0.0.4+nmu3_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/a/aumix/aumix_2.8-23_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cdrdao/cdrdao_1.2.2-18ubuntu3_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-bcop/compiz-fusion-bcop_0.8.2-0ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-documentation-en_2.28.1-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fglrx-installer/fglrx-modaliases_8.660-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-pilot/gnome-pilot_2.0.17-0ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gtick/gtick_0.4.2-1lenny1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines-qtcurve/gtk2-engines-qtcurve_0.69.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-style-qtcurve/kde-style-qtcurve_0.69.1-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libkdcraw7_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kdegraphics-strigi-plugins_4.3.2-0ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/konq-plugins/konqueror-plugins_4.3.0-0ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/konq-plugins/konq-plugins-l10n_4.3.0-0ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-adblock_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-akregator_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-autorefresh_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-babelfish_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-crashes_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-dirfilter_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-domtreeviewer_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-fsview_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-imagerotation_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-khtmlsettings_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-kimgallery_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-minitools_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-rellinks_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/konq-plugins/konqueror-plugin-searchbar_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-uachanger_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-validators_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugin-webarchiver_4.3.0-0ubuntu4_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/multipath-tools/kpartx_0.4.8-14ubuntu2_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libl/liblouis/liblouis-data_1.7.0-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libl/liblouis/liblouis0_1.7.0-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/phoronix-test-suite/phoronix-test-suite_2.0.0ga-0ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-gdata/python-gdata_1.2.4-0ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libl/liblouis/python-louis_1.7.0-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-guest-source_3.0.8-dfsg-1ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-qt_3.0.8-dfsg-1ubuntu1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xdotool/xdotool_20090330-1_i386.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-mathml/xfonts-mathml_2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 130.239.18.137 80]


```
How do I upgrade to Karmic?

---

### Post by RJARRRPCGP on 2009-10-30
Looks like your network hardware may be bad.

---

### Post by richlyn9 on 2009-10-30
Remember that Kramic has many features that are totally new like grub2 and it is advised to do a clean install to enjoy the features.

---

