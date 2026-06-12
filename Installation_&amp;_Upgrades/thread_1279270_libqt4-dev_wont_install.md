---
title: "libqt4-dev wont install"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by brynjulfr on 2009-09-30
First off, apologies if this is in the wrong forum, first time needing help on these forums.

I did a fresh install of 9.04 UNR onto my netbook. everything went well, but i cannot seem to install libqt4-dev package that I need. This package readily installed when I was using 8.10 standard ubuntu. I get an error like the following:

```
The following packages have unmet dependencies:
  libqt4-dev: Depends: libxext-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxrandr-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxmu-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libx11-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxt-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxrender-dev but it is not going to be installed
              Depends: libxcursor-dev but it is not going to be installed
              Depends: libxinerama-dev but it is not going to be installed
              Depends: libxi-dev but it is not going to be installed
              Depends: libfreetype6-dev but it is not going to be installed
              Depends: libglu1-xorg-dev but it is not going to be installed or
                       libglu1-mesa-dev but it is not going to be installed or
                       libglu-dev
              Depends: libxft-dev but it is not going to be installed
              Depends: libpq-dev but it is not going to be installed
              Depends: libssl-dev but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4.5.0-0ubuntu4) but it is not going to be installed
E: Broken packages

```Any help is appreciated.

---

### Post by cefn on 2009-12-21
I ran into a libqt-dev problem with a similar error message when I'd added a newer X repository with different 3d video card drivers. 

The dependencies for the 3D support of Qt are very strict and the newer version I was running from x-swat wasn't compatible. 

I had to rollback from the later version of X following this kind of procedure...
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/455300/comments/2](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/455300/comments/2) 
...and then I found libqt-dev installed flawlessly and I was able to compile and run some test cases with Qt.

---

