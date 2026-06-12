---
title: "using Canon PIXMA MP230 scanner with sane-based software"
date: 2013-09-29
forum: Hardware
---

### Post by karl_forner on 2013-09-29
In short, the scanner of my **Canon PIXMA MP230** was not working with the usual scan software, e.g. gscan2pdf, xsane etc...

The cause: Canon PIXMA MP230 scanner support has only be added to latest libsane 1.0.24, that is not yet released, so not yet available to ubuntu users.

The fix: 
I followed these steps to install latest libsane from source: [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)
But it was not working:

```
$ scanimage -V
scanimage (sane-backends) 1.0.24git; backend version 1.0.23
```

The backend version 1.0.23 was the old (system) version. 
The problem is conflicts between the files from (outdated) ubuntu packages and my newest libsane install. 
I could not just uninstall the libsane package, because too many other packages are dependent.

So my ugly hack was just to remove everything in the way:
```

cd /usr/lib/x86_64-linux-gnu/
sudo mkdir old
sudo mv libsane.a libsane.la libsane.so libsane.so.1 libsane.so.1.0.23 old/
sudo mv sane old/
# check
sudo ldconfig -v | grep libsane

```

Then everything is now just fine:
```
%scanimage -V
scanimage (sane-backends) 1.0.24git; backend version 1.0.24
$ scanimage -L
device `pixma:04A9175F' is a CANON Canon PIXMA MP230 multi-function peripheral
$ scanimage --test
```

---

### Post by samtux on 2014-02-05
Thanks, it worked properly!!!!

---

### Post by aikishugyo on 2014-02-05
This sounds like a really bad plan, which I do not recommend to anyone, as it is most likely to break your system in the future.
The HowTo is atrociously wrong, and should be corrected.

I fail to see why in Ubuntu one cannot not install SANE comfortably alongside your existing SANE, as would be the default if onr does not force it to do anything else (as the terrible HowTo does).

The linux README in the SANE source is quite clear on how to install it, Ubuntu is one of the common destination systems. 
Please read it and try that, as the method given in the HowTo for installing SANE and over-writing system files is very bad.

---

### Post by mrhaw on 2014-05-28
> *"Canon PIXMA MP230 scanner support has only be added to latest libsane 1.0.24"*
I followed that guide [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

Then I run sudo gedit /lib/udev/rules.d/40-libsane.rules ...

> This file was automatically created based on description files (*.desc)
# by sane-desc 3.5 from sane-backends 1.0.23


Fail...

I have set
include /etc/ld.so.conf.d/*.conf
include /usr/local/lib

// My /usr/local/lib only have python folders in it...


The only way my xubuntu14.04 can recognize the scanner is when I run sudo-sane-find-scanner

PIC: [https://drive.google.com/file/d/0B1UYVvax8n17UG5yd2g3SlVZV0E/edit?usp=sharing](https://drive.google.com/file/d/0B1UYVvax8n17UG5yd2g3SlVZV0E/edit?usp=sharing)

No other command will list it :(

---

