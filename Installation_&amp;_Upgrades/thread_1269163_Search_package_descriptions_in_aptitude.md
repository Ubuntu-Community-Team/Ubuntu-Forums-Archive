---
title: "Search package descriptions in aptitude"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by undecim on 2009-09-17
Can someone tell me how to search package descriptions for a keyword in aptitude? I can't seem to find this in the docs.

---

### Post by wojox on 2009-09-17
Is this it:

```
wojox@wojox:~$ sudo apt-cache show firefox-3.5
Package: firefox-3.5
Priority: optional
Section: universe/web
Installed-Size: 3524
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.5.2+nobinonly-0ubuntu0.9.04.1
Replaces: firefox-3.1
Provides: firefox-3.1, www-browser
Depends: fontconfig, psmisc, debianutils (>= 1.16), xulrunner-1.9.1 (>= 1.9.1), libasound2 (>> 1.0.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.16.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.1.1), firefox-3.5-branding | abrowser-3.5-branding
Recommends: ubufox
Suggests: firefox-3.5-gnome-support (= 3.5.2+nobinonly-0ubuntu0.9.04.1), latex-xft-fonts, libthai0
Conflicts: firefox-3.1 (<< 3.1~b4~hg20090317)
Filename: pool/universe/f/firefox-3.5/firefox-3.5_3.5.2+nobinonly-0ubuntu0.9.04.1_i386.deb
Size: 929502
MD5sum: 2d6591fb2ccac8c549d96c5a58a88392
SHA1: 2173241ade2fd246eabd6e4d436d5e72423d5548
SHA256: bed4fe6e91f13f0bc1b4ab1dacddbd6a659d6f765650707108e9c47289da7dd8
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: firefox-3.5
Priority: optional
Section: universe/web
Installed-Size: 3468
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.5~b4~hg20090330r24021+nobinonly-0ubuntu1
Replaces: firefox-3.1
Provides: firefox-3.1, www-browser
Depends: fontconfig, psmisc, debianutils (>= 1.16), xulrunner-1.9.1 (>= 1.9.1~b4~), libasound2 (>> 1.0.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.16.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.1.1), firefox-3.5-branding | abrowser-3.5-branding
Recommends: ubufox
Suggests: firefox-3.5-gnome-support (= 3.5~b4~hg20090330r24021+nobinonly-0ubuntu1), latex-xft-fonts, libthai0
Conflicts: firefox-3.1 (<< 3.1~b4~hg20090317)
Filename: pool/universe/f/firefox-3.5/firefox-3.5_3.5~b4~hg20090330r24021+nobinonly-0ubuntu1_i386.deb
Size: 911150
MD5sum: 5302267d2d5614887333c51cbbe499e0
SHA1: 6dc661c50aeb0990099041553249c8d541811df3
SHA256: 15cd6ea6d1680ddb9480cf8eb488f25866bd08229b8f6bc067f2a2a77087fd5d
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

---

### Post by undecim on 2009-09-17
No, I mean search for a new package by searching for a keyword in the description, like synaptic package manager does. For example, if I search for "browser" I want firefox to show up in the results (along with nautilus, konqueror, etc.)

---

### Post by undecim on 2009-09-29
found my answer: I use "~d" in front of my search term in "aptitude search" command or when using the search function in the aptitude gui.

---

