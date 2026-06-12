---
title: "firefox broken"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by pradtf on 2009-01-11
just did a new install last night of ubuntu.
firefox doesn't run or even install:

[I]sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
firefox is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-3.0-branding: Depends: firefox-3.0 (= 3.0.3+nobinonly-0ubuntu2) but 3.0.5+nobinonly-0ubuntu0.8.10.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/I]

after doing the suggested apt-get -f install:
[I]
E: Tar checksum failed, archive corrupted
E: Prior errors apply to /var/cache/apt/archives/firefox-3.0-branding_3.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/firefox-3.0-branding_3.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-3.0-branding_3.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/I]

anyone know what is happening?

---

### Post by Pumalite on 2009-01-11
Try:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by pradtf on 2009-01-11
thanks, but we are getting the same message after 
sudo apt-get -f install

the problem seems to be that 
E: Tar checksum failed, archive corrupted

so it seems we just have to wait till it is fixed.

---

### Post by taurus on 2009-01-11
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by pradtf on 2009-01-11
that got us a bit further in that some of it worked - guess the 'clean' got rid of the corrupt stuff that was on our computer. however, firefox still doesn't go.

what we will try is redo the install and just not upgrade right now.

thx for your help.

---

