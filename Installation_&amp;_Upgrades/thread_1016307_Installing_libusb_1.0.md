---
title: "Installing libusb 1.0"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by magicman5421 on 2008-12-19
I'd like to install fprint on my HP dv9500 Ubuntu 8.10 laptop so that I can use my fingerprint reader to authenticate sudo and login.
However, compiling it from source requires libusb 1.0. The latest version in the repo is 0.1. How do I update libusb? When I try to remove it in synaptic it asks me to remove most of ubuntu. Will building libusb 1.0 from source overwrite the old version or will there still be residual parts of it hanging around?
The link to libusb is [http://libusb.wiki.sourceforge.net/](http://libusb.wiki.sourceforge.net/).
Thanks

---

### Post by Kareeser on 2008-12-19
Looks like you might need to compile it from source:
[http://libusb.wiki.sourceforge.net/](http://libusb.wiki.sourceforge.net/)

---

### Post by magicman5421 on 2008-12-19
that's what i asked
will compiling from source overwrite the current version (0.1) or will it screw it up?

---

### Post by prsmk on 2009-01-07
The new library libusb v1.0 coexists with libusb v0.1. Download the source code and compile the libusb v1.0 library.

---

### Post by mous16 on 2009-02-27
You can use also the jaunty packages.

---

