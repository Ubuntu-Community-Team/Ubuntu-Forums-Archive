---
title: "configure error: GLIB not installed"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by AlphaLexman on 2009-10-22
I am trying to install vumeter-0.9.2.tar.gz. Downloaded, unpacked, good.

During ./configure I got this error:

> checking for glib-config... no
checking for GLIB - version >= 1.2.10... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.10 not installed - please install first ***
I did an apt-cache search glib and got alot of choices. Anyone know which package I need?
Also looked in synaptic and my best guess is:
Package = libglib1.2ldbl
Latest Version = 1.2.10-19build1

Although synaptic says I have libglib2.0-0 installed.

Is this a path, environment variable or install problem?

---

### Post by zvacet on 2009-10-23
Delette folder you get with unpacking,so you will have just vumeter-0.9.2.tar.gz. In terminal go to the directory where your package is and type 


```
sudo apt-get build-dep vumeter
```

That should give you all dependencies and after that you can compile.

---

### Post by AlphaLexman on 2009-10-23
Thanks, I did get it running last night. Probably the hard way. I had to install the original xmms (not xmms2), an old gtk, a gdm something. Although I haven't got the vumeter working with audacious yet.

---

