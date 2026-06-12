---
title: "Upgrade terrible!"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by jaxtabram on 2009-04-30
Lots of errors on upgrading to Jaunty.
In the end it said my system may now be unstable ...it is.
It has gone from being smooth and fast and problem free to slow jittery ...upgrade manager no longer works mouse hardly works and this is only what is obvious in the first ten minutes of rebooting.
I installed from a server.

Do I now have to reinstall my Intrepid I bex all over again?
I'm not a comp whizz ...I know nothing about command line stuff.
I'm well pissed off.

---

### Post by lisati on 2009-04-30
I don't blame you for being annoyed......
Before you go and reinstall Intrepid (which is always an option), are there any specific errors you'd like us to help you with?

---

### Post by jaxtabram on 2009-04-30
> **lisati said:**
> I don't blame you for being annoyed......
Before you go and reinstall Intrepid (which is always an option), are there any specific errors you'd like us to help you with?
I'm afraid my knpowledge of whats wrong is almost nil.
All I know so far is my cursor is flickering and jumpy ...i typre this and have to wait for the text to complete ...to catch up with my typing ...I try to choose anything and it takes an age to load ...to even allow me to pick pictures music whatever.
The whole thimng has become a slow jittery mess I'm afraid.
What has amazed me is the speed of your response!
Thankyou.

---

### Post by jaxtabram on 2009-04-30
Is it possible to fix from the server?
If not I'm going to have to reinstall Ibex which I pressume means I'll lose everything and I'm going to be very wary of upgrading again.
Waiting for the text to catch up with my typing is going to be impossible to live with.
Just trying to choose to minimise the window is a slow process.
I've only been a Linux user for about a month!

---

### Post by abn91c on 2009-04-30
open a terminal type **[COLOR="Blue"]sudo dpkg --configure -a[/COLOR]** followed by[COLOR="blue"]** sudo apt-get install -f**[/COLOR] tell us what happens

---

### Post by jaxtabram on 2009-05-01
> **abn91c said:**
> open a terminal type **[COLOR=Blue]sudo dpkg --configure -a[/COLOR]** followed by[COLOR=blue]** sudo apt-get install -f**[/COLOR] tell us what happens

Thankyou very much for your time it is much appreciated.
This is what I got  ...sorry about the size of it.

-=-=-==-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-0=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-


sudo dpkg -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
jack@jack-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libstrigiqtdbusclient0 cacao-oj6-jre-lib libarts1c2a libartsc0
  ttf-wqy-zenhei airstrike-common linux-headers-2.6.27-7 pinball-data
  libwxgtk2.6-0 gnome-icon-theme-gartoon libgfortran2 python-pygame
  ttf-kannada-fonts libkdegames4 linux-headers-2.6.27-7-generic libqt4-core
  edubuntu-artwork-usplash libaccess-bridge-java librasqal0 libalut0
  libqt4-gui ttf-telugu-fonts libwxbase2.6-0 libcaptury0 tzdata-java mbr
  libphysfs-1.0-0 libpigment0.3-5 cacao-oj6-jre-headless python-dateutil
  gcc-4.2-base libdvdread3 bomberclone-data kdebase-workspace-data
  enigma-level-previews rhino liblua5.1-0 ttf-oriya-fonts enigma-doc
  libcapseo0 ca-certificates-java ttf-bengali-fonts xutils-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up update-manager-core (1:0.111.8) ...
file does not exist: /usr/lib/python2.5/site-packages/computerjanitor/exc_tests.py
pycentral: pycentral pkginstall: error byte-compiling files (49)
pycentral pkginstall: error byte-compiling files (49)
dpkg: error processing update-manager-core (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gst0.10 (0.10.14-1ubuntu1) ...
file does not exist: /usr/lib/python2.6/dist-packages/pygst.py
pycentral: pycentral pkginstall: error byte-compiling files (9)
pycentral pkginstall: error byte-compiling files (9)
dpkg: error processing python-gst0.10 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pgm:
 python-pgm depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing python-pgm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-elisa:
 python-elisa depends on python-gst0.10; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
        Package python-gst0.10 is not configured yet.
 python-elisa depends on python-pgm (>= 0.3.9); however:
  Package python-pgm is not configured yet.
dpkg: error processing python-elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-good:
 elisa-plugins-good depends on python-elisa (>= 0.5.28); however:
  Package python-elisa is not configured yet.
 elisa-plugins-good depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-bad:
 elisa-plugins-bad depends on python-elisa (>= 0.5.28); however:
  Package python-elisa is not configured yet.
 elisa-plugins-bad depends on elisa-plugins-good (>= 0.5.28); however:
  Package elisa-plugins-good is not configured yet.
 elisa-plugins-bad depends on python-pgm (>= 0.3.5); however:
  Package python-pgm is not configured yet.
 elisa-plugins-bad depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-bad (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa:
 elisa depends on python-elisa (= 0.5.28-1ubuntu1); however:
  Package python-elisa is not configured yet.
 elisa depends on elisa-plugins-good; however:
  Package elisa-plugins-good is not configured yet.
 elisa depends on elisa-plugins-bad; however:
  Package elisa-plugins-bad is not configured yet.
 elisa depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-ugly:
 elisa-plugins-ugly depends on elisa-plugins-bad; however:
  Package elisa-plugins-bad is not configured yet.
dpkg: error processing elisa-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on python-gst0.10 (>= 0.10.12); however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-plugins (>= 2.26.1-0ubuntu5); however:
  Package totem-plugins is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.111.8); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 update-manager-core
 python-gst0.10
 gnome-app-install
 apturl
 python-pgm
 python-elisa
 elisa-plugins-good
 elisa-plugins-bad
 elisa
 elisa-plugins-ugly
 totem-plugins
 totem
 ubufox
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
jack@jack-desktop:~$

---

### Post by jaxtabram on 2009-05-01
Why have they removed the minimise clicky thingy?
Pain in the ****.
What kind of upgrade makes a simple operation like minimising the window ...go from one click to two?

---

### Post by abn91c on 2009-05-01
> **jaxtabram said:**
> Why have they removed the minimise clicky thingy?
Pain in the ****.
What kind of upgrade makes a simple operation like minimising the window ...go from one click to two?
the first command has **two** dashes [SIZE="4"]sudo dpkg --configure -a[/SIZE]

---

### Post by jaxtabram on 2009-05-01
> **abn91c said:**
> the first command has **two** dashes [SIZE=4]sudo dpkg --configure -a[/SIZE]


Similar report I think ...


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-==-=-=-=-=-=-=-=-=-=-=-=0-=-=-=-=-=-=-=-=-=-=-=-=-=--=-==-=-=-=-=-=-=

sudo dpkg --configure -a
[sudo] password for jack: 
Setting up update-manager-core (1:0.111.8) ...
file does not exist: /usr/lib/python2.5/site-packages/computerjanitor/exc_tests.py
pycentral: pycentral pkginstall: error byte-compiling files (49)
pycentral pkginstall: error byte-compiling files (49)
dpkg: error processing update-manager-core (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gst0.10 (0.10.14-1ubuntu1) ...
file does not exist: /usr/lib/python2.6/dist-packages/pygst.py
pycentral: pycentral pkginstall: error byte-compiling files (9)
pycentral pkginstall: error byte-compiling files (9)
dpkg: error processing python-gst0.10 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on python-gst0.10 (>= 0.10.12); however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-good:
 elisa-plugins-good depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.111.8); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pgm:
 python-pgm depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing python-pgm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa:
 elisa depends on elisa-plugins-good; however:
  Package elisa-plugins-good is not configured yet.
 elisa depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-plugins (>= 2.26.1-0ubuntu5); however:
  Package totem-plugins is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-bad:
 elisa-plugins-bad depends on elisa-plugins-good (>= 0.5.28); however:
  Package elisa-plugins-good is not configured yet.
 elisa-plugins-bad depends on python-pgm (>= 0.3.5); however:
  Package python-pgm is not configured yet.
 elisa-plugins-bad depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-bad (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-elisa:
 python-elisa depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
 python-elisa depends on python-pgm (>= 0.3.9); however:
  Package python-pgm is not configured yet.
dpkg: error processing python-elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-ugly:
 elisa-plugins-ugly depends on elisa-plugins-bad; however:
  Package elisa-plugins-bad is not configured yet.
dpkg: error processing elisa-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-manager-core
 python-gst0.10
 totem-plugins
 elisa-plugins-good
 update-manager
 python-pgm
 elisa
 gnome-app-install
 totem
 elisa-plugins-bad
 python-elisa
 elisa-plugins-ugly
 update-notifier
 apturl
 ubufox
jack@jack-desktop:~$

---

### Post by abn91c on 2009-05-01
maybe so sudo aptitude  reinstall update-manager-core, since is looking for that package

---

### Post by jaxtabram on 2009-05-01
> **abn91c said:**
> maybe so sudo aptitude  reinstall update-manager-core, since is looking for that package
How do I reinstall update manager?
I wish I could buy you a pint.

---

### Post by mafaldaspeaks on 2009-05-01
> **lisati said:**
> I don't blame you for being annoyed......
Before you go and reinstall Intrepid (which is always an option), are there any specific errors you'd like us to help you with?

Hi, lisati! May I include myself here? My desktop just finished installing and asked to be restarted. I did so and it went through the usual initial stages until just before the desktop appeared--I mean, the screen froze with all these horizontal bar lines. Nothing's working. Can you suggest what to do?

---

### Post by abn91c on 2009-05-01
> **jaxtabram said:**
> How do I reinstall update manager?
I wish I could buy you a pint.
sudo aptitude reinstall <package name here> will reinstall any package

---

### Post by jaxtabram on 2009-05-01
> **abn91c said:**
> maybe so sudo aptitude  reinstall update-manager-core, since is looking for that package
Ahhh ...doing it now and a very big thanks mate ...I have to go shortly so I'm hoping this bit will change things ...

---

### Post by abn91c on 2009-05-01
> **jaxtabram said:**
> Ahhh ...doing it now and a very big thanks mate ...I have to go shortly so I'm hoping this bit will change things ...
Welcome Jax, I am off to work too, and see if I can avoid someone coughing the swine flu on me, I am a Nurse :-)

---

### Post by lisati on 2009-05-01
> **mafaldaspeaks said:**
> Hi, lisati! May I include myself here? My desktop just finished installing and asked to be restarted. I did so and it went through the usual initial stages until just before the desktop appeared--I mean, the screen froze with all these horizontal bar lines. Nothing's working. Can you suggest what to do?

Might be good for a separate discussion.......

---

### Post by jaxtabram on 2009-05-01
> **abn91c said:**
> Welcome Jax, I am off to work too, and see if I can avoid someone coughing the swine flu on me, I am a Nurse 
Oh dear ...stay safe.
I'm afraid I got an even bigger report this time ..as I type this ...the texyt is actually happening as I type instead of playing catch up ...does this mean alls well?

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-==-=-=-=-=-=0-=-===-=-=-=-=-=-=-=-=-=-=-=-==-=-=-=-=-

sudo aptitude reinstall update-manager-core
[sudo] password for jack: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  update-manager-core 
The following packages will be REMOVED:
  airstrike-common{u} bomberclone-data{u} ca-certificates-java{u} 
  cacao-oj6-jre-headless{u} cacao-oj6-jre-lib{u} 
  edubuntu-artwork-usplash{u} enigma-doc{u} enigma-level-previews{u} 
  gcc-4.2-base{u} gnome-icon-theme-gartoon{u} kdebase-workspace-data{u} 
  libaccess-bridge-java{u} libalut0{u} libarts1c2a{u} libartsc0{u} 
  libcapseo0{u} libcaptury0{u} libdvdread3{u} libgfortran2{u} 
  libkdegames4{u} liblua5.1-0{u} libopenal1{u} libphysfs-1.0-0{u} 
  libpigment0.3-5{u} libqt4-core{u} libqt4-gui{u} librasqal0{u} 
  libstrigiqtdbusclient0{u} libwxbase2.6-0{u} libwxgtk2.6-0{u} 
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} mbr{u} 
  pinball-data{u} python-dateutil{u} python-pygame{u} rhino{u} 
  ttf-bengali-fonts{u} ttf-kannada-fonts{u} ttf-oriya-fonts{u} 
  ttf-telugu-fonts{u} ttf-wqy-zenhei{u} tzdata-java{u} xutils-dev{u} 
The following partially installed packages will be configured:
  apturl elisa elisa-plugins-bad elisa-plugins-good elisa-plugins-ugly 
  gnome-app-install python-elisa python-gst0.10 python-pgm totem 
  totem-plugins ubufox update-manager update-notifier 
0 packages upgraded, 0 newly installed, 1 reinstalled, 44 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 220MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 175218 files and directories currently installed.)
Removing airstrike-common ...
Removing bomberclone-data ...
Removing edubuntu-artwork-usplash ...
Removing enigma-doc ...
Removing enigma-level-previews ...
Removing libgfortran2 ...
Removing gcc-4.2-base ...
Removing gnome-icon-theme-gartoon ...
Removing kdebase-workspace-data ...
Removing libalut0 ...
Removing libarts1c2a ...
Removing libartsc0 ...
Removing libcaptury0 ...
Removing libcapseo0 ...
Removing libdvdread3 ...
Removing libkdegames4 ...
Removing liblua5.1-0 ...
Removing libopenal1 ...
Removing libphysfs-1.0-0 ...
Removing libpigment0.3-5 ...
Removing libqt4-core ...
Removing libqt4-gui ...
Removing librasqal0 ...
Removing libstrigiqtdbusclient0 ...
Removing libwxgtk2.6-0 ...
Removing libwxbase2.6-0 ...
Removing linux-headers-2.6.27-7-generic ...
Removing linux-headers-2.6.27-7 ...
Removing mbr ...
Removing pinball-data ...
Removing python-dateutil ...
Removing python-pygame ...
Removing ttf-bengali-fonts ...
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-bengali-fonts
Removing ttf-kannada-fonts ...
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/ttf-indic-fonts-core
Removing ttf-oriya-fonts ...
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-oriya-fonts
Removing ttf-telugu-fonts ...
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-telugu-fonts
Removing ttf-wqy-zenhei ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/wqy
Removing xutils-dev ...
Removing rhino ...
Removing ca-certificates-java ...
Removing cacao-oj6-jre-headless ...
Removing cacao-oj6-jre-lib ...
Removing libaccess-bridge-java ...
Removing tzdata-java ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up update-manager-core (1:0.111.8) ...
file does not exist: /usr/lib/python2.5/site-packages/computerjanitor/exc_tests.py
pycentral: pycentral pkginstall: error byte-compiling files (49)
pycentral pkginstall: error byte-compiling files (49)
dpkg: error processing update-manager-core (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gst0.10 (0.10.14-1ubuntu1) ...
file does not exist: /usr/lib/python2.6/dist-packages/pygst.py
pycentral: pycentral pkginstall: error byte-compiling files (9)
pycentral pkginstall: error byte-compiling files (9)
dpkg: error processing python-gst0.10 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pgm:
 python-pgm depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing python-pgm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-elisa:
 python-elisa depends on python-gst0.10; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                                                                                                        No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                                                                                        No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                                                                                                      No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                                                                                                        Package python-gst0.10 is not configured yet.
 python-elisa depends on python-pgm (>= 0.3.9); however:
  Package python-pgm is not configured yet.
dpkg: error processing python-elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-good:
 elisa-plugins-good depends on python-elisa (>= 0.5.28); however:
  Package python-elisa is not configured yet.
 elisa-plugins-good depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-bad:
 elisa-plugins-bad depends on python-elisa (>= 0.5.28); however:
  Package python-elisa is not configured yet.
 elisa-plugins-bad depends on elisa-plugins-good (>= 0.5.28); however:
  Package elisa-plugins-good is not configured yet.
 elisa-plugins-bad depends on python-pgm (>= 0.3.5); however:
  Package python-pgm is not configured yet.
 elisa-plugins-bad depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-bad (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa:
 elisa depends on python-elisa (= 0.5.28-1ubuntu1); however:
  Package python-elisa is not configured yet.
 elisa depends on elisa-plugins-good; however:
  Package elisa-plugins-good is not configured yet.
 elisa depends on elisa-plugins-bad; however:
  Package elisa-plugins-bad is not configured yet.
 elisa depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-ugly:
 elisa-plugins-ugly depends on elisa-plugins-bad; however:
  Package elisa-plugins-bad is not configured yet.
dpkg: error processing elisa-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on python-gst0.10 (>= 0.10.12); however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-plugins (>= 2.26.1-0ubuntu5); however:
  Package totem-plugins is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.111.8); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 update-manager-core
 python-gst0.10
 gnome-app-install
 apturl
 python-pgm
 python-elisa
 elisa-plugins-good
 elisa-plugins-bad
 elisa
 elisa-plugins-ugly
 totem-plugins
 totem
 ubufox
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up update-manager-core (1:0.111.8) ...
file does not exist: /usr/lib/python2.5/site-packages/computerjanitor/exc_tests.py
pycentral: pycentral pkginstall: error byte-compiling files (49)
pycentral pkginstall: error byte-compiling files (49)
dpkg: error processing update-manager-core (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gst0.10 (0.10.14-1ubuntu1) ...
file does not exist: /usr/lib/python2.6/dist-packages/pygst.py
pycentral: pycentral pkginstall: error byte-compiling files (9)
pycentral pkginstall: error byte-compiling files (9)
dpkg: error processing python-gst0.10 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on python-gst0.10 (>= 0.10.12); however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-good:
 elisa-plugins-good depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.111.8); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pgm:
 python-pgm depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing python-pgm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa:
 elisa depends on elisa-plugins-good; however:
  Package elisa-plugins-good is not configured yet.
 elisa depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-plugins (>= 2.26.1-0ubuntu5); however:
  Package totem-plugins is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-bad:
 elisa-plugins-bad depends on elisa-plugins-good (>= 0.5.28); however:
  Package elisa-plugins-good is not configured yet.
 elisa-plugins-bad depends on python-pgm (>= 0.3.5); however:
  Package python-pgm is not configured yet.
 elisa-plugins-bad depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing elisa-plugins-bad (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-elisa:
 python-elisa depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
 python-elisa depends on python-pgm (>= 0.3.9); however:
  Package python-pgm is not configured yet.
dpkg: error processing python-elisa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of elisa-plugins-ugly:
 elisa-plugins-ugly depends on elisa-plugins-bad; however:
  Package elisa-plugins-bad is not configured yet.
dpkg: error processing elisa-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on apturl (>= 0.1.2ubuntu1); however:
  Package apturl is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-manager-core
 python-gst0.10
 totem-plugins
 elisa-plugins-good
 update-manager
 python-pgm
 elisa
 gnome-app-install
 totem
 elisa-plugins-bad
 python-elisa
 elisa-plugins-ugly
 update-notifier
 apturl
 ubufox
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

jack@jack-desktop:~$

---

### Post by emarkay on 2009-05-01
> **mafaldaspeaks said:**
> Hi, lisati! May I include myself here? My desktop just finished installing and asked to be restarted. I did so and it went through the usual initial stages until just before the desktop appeared--I mean, the screen froze with all these horizontal bar lines. Nothing's working. Can you suggest what to do?

For sure, this is a separate issue - do a search for your graphics card type first - there are some big ATI issues and lesser Intel and NVIDIA issues in 9.04.  If  nothing seems similar, post a new thread.

---

### Post by jaxtabram on 2009-05-01
> **emarkay said:**
> For sure, this is a separate issue - do a search for your graphics card type first - there are some big ATI issues and lesser Intel and NVIDIA issues in 9.04.  If  nothing seems similar, post a new thread.
I'm not to clued up about all these issues apart from the fact I'm having them.
I'll sleep on it but me thinks  I'm going back to my first love ...Intrepid.
Soft smooth and fast.
Your a great bunch ...thanks ...I might be back ...

---

### Post by sailthesea on 2009-05-01
How did you perform your upgrade? I'm wondering how updating from Intrepid to Jaunty with update manager performs against disc upgrades or fresh installs Maybe an underlying wobble in your original setup is being amplified? I've noticed a bit of "fuzziness" about things with jaunty but nothing like your problem despite using a pretty old lappy 
 Hope you get fixed!:)

---

### Post by jaxtabram on 2009-05-02
> **sailthesea said:**
> How did you perform your upgrade? I'm wondering how updating from Intrepid to Jaunty with update manager performs against disc upgrades or fresh installs Maybe an underlying wobble in your original setup is being amplified? I've noticed a bit of "fuzziness" about things with jaunty but nothing like your problem despite using a pretty old lappy 
 Hope you get fixed!:)
I installed Intrepid from disc and have downloaded and updated stuff and it has worked without a blip then came the offer to download the upgrade ...all gone wobbly since then.
I'm taking it out tomorrow and going back to Intrepid.

---

### Post by bimmermz3 on 2009-05-02
i've had a similar problem with my update.  i can't even do anything other than get to the terminal at the log in screen....really frustrating.  i downloaded Intrepid but when i try to reinstall, it won't recognize it.  am i missing a file that's not on ubuntu's website?  is there an installer i am forgetting?  i see about uNetBootin but i want to install w/ a CD.  
i'm getting really bummed over here.

---

### Post by neu2buntu on 2009-05-02
```
i see about uNetBootin but i want to install w/ a CD.  
i'm getting really bummed over here.
```    you can use use unetbootin to make a live usb or install from the .iso image of ubuntu and i think also from the net ie netinstall   .... im not sure how to or if it is possible to do this from the terminal as i think unetbootin needs a graphical interface.... you could use unetbootin from another computer in windows or linux and make your live usb

---

### Post by bimmermz3 on 2009-05-02
maybe you can help me fix jaunty then...
i updated to jaunty and after the login screen it shows the desktop for a second and then goes all black other than the mouse.  that's it.  i uninstalled compiz thinking maybe that was the problem, but no.  any other clue.  i am running 
intel graphics

---

### Post by neu2buntu on 2009-05-02
hmmm this is tricky territory for me....  try the basics 
(1) i would say ctrl-alt-backspace but i think it is disabled in jaunty
(2) command :- startx 
(3) command :- compiz
(4) ctrl-alt-f7    (try f1 through to f7) f7 is the default screen
(5) command:- sudo dpkg-reconfigure -phigh xserver-xorg                  (this update xorg.conf file)
 try these options first to see if any joy!!!

---

### Post by neu2buntu on 2009-05-02
also command ```
cat /var/log/Xorg.0.log
```
this may show what is going on with the xserver....

---

### Post by bimmermz3 on 2009-05-02
i thank you for your help....i actually just broke down and reinstalled Intrepid.  Maybe i'll try jaunty after some bugs are worked out.
thanks again!
cheers

---

### Post by neu2buntu on 2009-05-02
i too upgraded from 8.10 to 9.04, but was having some audio issues, so just backed up some files to external hdd and then did a clean reinstall of 9.04 and things seem good... only problem really now is wifi led on my aa1, but il look into that soon....   so maybe a clean install would be ok for you too

---

### Post by mafaldaspeaks on 2009-05-03
Good news. After the nightmare of spending a whole day upgrading my family's desktop from 8.10 to 9.04 and having to see the display freeze without any response at all, I tried rebooting on a live CD (I originally had 8.04 only and then was able to download 9.04 on the laptop) as user ZEEX very helpfully suggested to me. First I went to BIOS so as to change the boot settings, making the CD drive the first one. Then I simply restarted with the live CD inside the drive and jaunty installed as smooth as anything--and finished within one hour! It's working quite well now.:P

---

