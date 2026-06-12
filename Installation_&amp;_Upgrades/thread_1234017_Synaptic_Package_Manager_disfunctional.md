---
title: "Synaptic Package Manager disfunctional"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by thiart on 2009-08-07
Hi there

I just (re)installed Ubuntu after a system crash when my laptop's battery ran out of steam (gas?) (electrons?). Anyway now my Synaptic Package Manager doesn't work anymore; this is what I get when I push the reload button:

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


HELP PLEASE!

PS: Yes, my internet connection is up and functioning (otherwise I could not post this message).

---

### Post by wojox on 2009-08-07
Go to System > Admin > Software Sources.
First tab look for Download from.
Pick a new server.

---

