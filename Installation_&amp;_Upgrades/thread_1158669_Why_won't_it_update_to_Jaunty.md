---
title: "Why won't it update to Jaunty?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by Ascyron on 2009-05-13
I'm running Ubuntu 8.10, and looking to upgrade to 9.04. I open the Update Manager, see the bit where it says "new distribution release '9.04' is available", and click Upgrade.
It spends about 5 minutes downloading files, then throws me this message:


W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.



It then closes the installer.

I've tried three times now, always gives that exact same message.
What's the problem here? Is there a way I can get around it? Any suggestions at all?

---

### Post by zvacet on 2009-05-14
See if your system is updated

```
sudo apt-get update
```
 
and then 

```
sudo do-release-upgrade -d
```

---

### Post by alphacrucis2 on 2009-05-14
> **zvacet said:**
> See if your system is updated

```
sudo apt-get update
```
 
and then 

```
sudo do-release-upgrade -d
```

I always thought -d was for development releases?

---

### Post by Ascyron on 2009-05-14
While doing "sudo apt-get update", it gave the following error messages...


Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Sources
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Packages
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Sources
  Unable to connect to nz.archive.ubuntu.com http:
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  Unable to connect to nz.archive.ubuntu.com http:

E: Some index files failed to download, they have been ignored, or old ones used instead.




Is it possible that the problem is with the server I'm downloading the updates from? If that is the case, how would I download from a different server?

---

### Post by Kevbert on 2009-05-14
It looks like the server may be in the process of being updated. You have two choices, wait a while or change your server via Software Sources. Open System-Admin-Software Sources. Under the Updates Tab in the 'Download from' box select 'Other', click on 'Select best server' and then 'Close'. Close Software Sources.
Now in terminal enter
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
and you should be back in business.

---

### Post by Ascyron on 2009-05-14
I managed to get "sudo apt-get update" to work, but when doing "sudo do-release-upgrade" in the terminal, it gave the following error:



Calculating the changes

Error authenticating some packages 

It was not possible to authenticate some packages. This may be a 
transient network problem. You may want to try again later. See below 
for a list of unauthenticated packages. 

acpid 
apturl 
bluetooth 
bluez 
bluez-alsa 
bluez-cups 
bluez-gstreamer 
bluez-utils 
brasero 
checkbox 
checkbox-gtk 
compizconfig-backend-gconf 
consolekit 
cups 
cups-bsd 
cups-client 
cups-common 
ekiga 
evince 
evolution-exchange 
gnome-about 
gnome-app-install 
gnome-applets 
gnome-applets-data 
gnome-desktop-data 
gnome-settings-daemon 
gnome-system-tools 
hwtest 
hwtest-gtk 
libbluetooth3 
libbrasero-media0 
libck-connector0 
libcups2 
libcupsimage2 
libevdocument1 
libevview1 
libgl1-mesa-dri 
libgl1-mesa-glx 
libglu1-mesa 
libgnome-desktop-2-11 
libgweather-common 
libgweather1 
libical0 
libnautilus-extension1 
libpam-ck-connector 
libqt4-assistant 
libqt4-core 
libqt4-dbus 
libqt4-designer 
libqt4-help 
libqt4-network 
libqt4-opengl 
libqt4-qt3support 
libqt4-script 
libqt4-sql 
libqt4-sql-mysql 
libqt4-svg 
libqt4-test 
libqt4-webkit 
libqt4-xml 
libqt4-xmlpatterns 
libqtcore4 
libqtgui4 
libsoup-gnome2.4-1 
libsoup2.4-1 
libudev0 
libvolume-id1 
mesa-utils 
nautilus 
nautilus-data 
notification-daemon 
python-cupshelpers 
qt4-qtconfig 
screen-profiles 
splix 
synaptic 
system-config-printer-common 
system-config-printer-gnome 
ubuntu-docs 
udev 
update-manager 
update-manager-core 


Restoring original system state

Aborting




I'll keep trying in case it is a "transient network problem" like it said, but if that isn't the case... ideas?

---

### Post by Kevbert on 2009-05-14
Prior to updating to Jaunty you want to make sure all Intrepid upgrades are installed then do a distribution upgrade to get Jaunty packages (dist-upgrade).
It may be that you have one or two broken packages which you can check with
```
sudo apt-get install -f
```
Have you tried switching to the main server in Software Sources ?  Please note that the best server may not be in your country (N.Z). I'm in the UK and have even used Czech servers in the past.

---

### Post by Ascyron on 2009-05-16
I've worked out how to get it to work... thanks for everything :D

---

