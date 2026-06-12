---
title: "Partial upgrade"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by rapattack1 on 2008-12-03
Hi I have no understanding of what a Partial upgrade is and if I need it. I did the partial upgrade on a previous install of ubuntu that I had on my notebook but things got too slow. I am not sure if I was pushing it with the system specs...I dunno what a partial upgrade does?
I went back to Ubuntu 7 because it was too slow and now after doing update/upgrade it is asking if I want to install the partial upgrade again. I tried via the terminal this time and this is what I am getting:
carolyn@carolyn-laptop:~$ sudo bash
[sudo] password for carolyn:
root@carolyn-laptop:~# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Sources
Fetched 3B in 2s (1B/s)  
Reading package lists... Done
root@carolyn-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  compiz compiz-core compiz-gnome compiz-plugins cupsys ekiga evince f-spot
  gedit gedit-common gij gimp gimp-data gimp-print gimp-python
  gnome-app-install gnome-applets gnome-applets-data gnome-panel
  gnome-panel-data gnome-power-manager gnome-system-monitor gnupg
  gstreamer0.10-plugins-good gthumb human-theme iproute libgcj-bc libgimp2.0
  libgphoto2-2 libgphoto2-port0 libhsqldb-java libpam-modules libsane
  libsndfile1 libwnck-common linux-headers-generic linux-image-generic
  linux-restricted-modules-generic nautilus nautilus-data notification-daemon
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-math openoffice.org-style-human openoffice.org-writer pidgin
  pidgin-data poppler-utils python-gnome2-desktop python-gnome2-extras
  python-uno python2.4 python2.4-minimal python2.5 python2.5-minimal
  restricted-manager rhythmbox rss-glx ssl-cert ttf-dejavu ttf-indic-fonts
  ubuntu-artwork ubuntu-desktop update-notifier wvdial xsane xsane-common
  xserver-xorg-video-all yelp
0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
root@carolyn-laptop:~# 

Ultimately I don't want things to slow down like they did before. The cpu on this machine is 660mhz and the ram is 256mb.

I did google this time and last time but really don't quite understand.

---

### Post by xarte on 2008-12-16
I keep getting a failed 'partial upgrade' in the updates too. Luckily it's not affecting performace as yet but is frustrating. Does anyone know what is going on? All the posts my search is bringing up are to do with upgrading to Intrepid, this is a partial update on Hardy.

---

### Post by xarte on 2008-12-17
Found this 

[http://ubuntuforums.org/archive/index.php/t-763874.html](http://ubuntuforums.org/archive/index.php/t-763874.html)

currently trying out the last solution (mark all upgrades in 'synaptic package manager') and it's now downloading an hour-plus worth of packages.

Edited to add: Urgh, disaster. Packages broke, and my ham-fisted attempts to 'fix' things... well lets just say a clean install was called for.

---

### Post by rapattack1 on 2008-12-17
Gee i can't get into the drive with Ubuntustudio to try this out since I changed the power supply. I have plain ubuntu on the primary drive which is what I am using now and  ubuntustudio on the secondary drive. Something is haywire because also the keyboard doesn't work when loading. Like when you want to go into the bios or select in grub. I am not sure what to do.

---

