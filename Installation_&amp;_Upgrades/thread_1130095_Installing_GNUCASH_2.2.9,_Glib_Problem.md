---
title: "Installing GNUCASH 2.2.9, Glib Problem"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Marikawn on 2009-04-19
Hello,

I was trying to install the GNUCASH program from source but during the ./configure stage it said it required Glib 2.6.0 or greater. Well I looked into the synaptic package manager and i couldn't find the package so I went to the website
**[ftp://ftp.gnome.org/pub/gnome/sources/glib/](ftp://ftp.gnome.org/pub/gnome/sources/glib/)** That gnucash referred me to download the latest version. Well I did and built it from source but now I am getting this error message.

> checking for GLIB - version >= 2.6.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.9.6, but GLIB (2.16.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files


How can I fix it? I have tried uninstalling liblib2.0-0 but doing that would uninstall ALOT of essential packages. is there a way to fix this or maybe to uninstall this package but not it's dependencies?

Thanks in advance :D

-Jim

---

### Post by ptn107 on 2009-04-19
Ubuntu 9.04 includes gnucash 2.2.6 in the repositories.  The changes made in 2.2.9 are mostly bug fixes.  Is there a reason why 2.2.6 will not do?

---

### Post by ptn107 on 2009-04-19
**Update:

Saïvann Carignan has a PPA which usually contains the latest version of gnucash.  You could try that.

[https://edge.launchpad.net/~saivann/+archive/ppa](https://edge.launchpad.net/~saivann/+archive/ppa) for info.

or add:

deb [http://ppa.launchpad.net/saivann/ppa/ubuntu](http://ppa.launchpad.net/saivann/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/saivann/ppa/ubuntu](http://ppa.launchpad.net/saivann/ppa/ubuntu) jaunty main

to your /etc/apt/sources.list file.  Don't forget to import the PGP key for authentication.

---

