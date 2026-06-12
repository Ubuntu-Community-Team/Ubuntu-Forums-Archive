---
title: "ubuntu as file server....."
date: 2008-08-19
forum: General Help
---

### Post by devinloretz on 2008-08-19
I am following the directions on this site to setup my new Ubuntu system with my Mac:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

and when I got to this code line:

sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot

There were some problems and I am not sure what to do...here is a bit of what it says at the end...



gpg: WARNING: unsafe ownership on configuration file `/home/devinloretz/.gnupg/gpg.conf'
gpg: skipped "Jonas Smedegaard <dr@jones.dk>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

  dpkg-genchanges  >../netatalk_2.0.3-9_i386.changes
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
dpkg-buildpackage: warning: Failed to sign .dsc and .changesfile




Help please =D

---

### Post by devinloretz on 2008-08-19
bump

---

### Post by devinloretz on 2008-08-20
Anyone have anything?

I reinstalled Ubuntu and started the whole process over again. 

This time I noticed when I enter:

sudo apt-get source netatalk

I get :

gpg: WARNING: unsafe ownership on configuration file `/home/devinloretz/.gnupg/gpg.conf'
gpg: Signature made Fri 04 Apr 2008 06:51:18 PM PDT using DSA key ID C02440B8
gpg: Can't check signature: public key not found
dpkg-source: extracting netatalk in netatalk-2.0.3
dpkg-source: unpacking netatalk_2.0.3.orig.tar.gz
dpkg-source: applying ./netatalk_2.0.3-9.diff.gz



So I have part of the same error from later one but this is the first instance.

---

