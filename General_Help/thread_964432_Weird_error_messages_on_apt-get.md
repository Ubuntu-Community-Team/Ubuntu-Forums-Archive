---
title: "Weird error messages on apt-get"
date: 2008-10-30
forum: General Help
---

### Post by sdlyr8 on 2008-10-30
Hey I have had a bunch of weird error messages that come up every time I do a [FONT="Courier New"]sudo apt-get install[/FONT] and it's really starting to bother me. anyone know how to fix it? 


> $ sudo apt-get install libnet6-1.3-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnet6-1.3-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9 (1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1) ...
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.3+build1+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | xulrunner; however:
  Package firefox is not configured yet.
  Package firefox-2 is not installed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape-browser is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-gecko is not installed.
  Package epiphany-webkit is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package midbrowser is not installed.
  Package xulrunner is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on xulrunner-1.9 (>= 1.9~rc1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
 sun-java6-plugin
 yelp
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by potayto9 on 2008-11-01
I have the same problem.

---

