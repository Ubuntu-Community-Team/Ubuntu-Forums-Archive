---
title: "Need help installing konversation-1.2-alpha6"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by ROY.G.BIV on 2009-09-02
So, I download the .tar.bz2 file... only to find that ./configure, make, make install or any other of the standard tarball commands needed for installation do not work... There aren't any instructions anywhere either. I'm currently running the alpha4 version of Konversation and really want to upgrade. Can someone help me?

See screenshot for files in first folder.

---

### Post by ROY.G.BIV on 2009-09-03
Okay, an update. I've almost got it installed... apparently installing a KDE tarball is much different than installing a Gmone one. I still need help though. Here's the process:

tar -xjf konversation-1.2-alpha6.tar.bz2
cd konversation-1.2-alpha6/
mkdir build
cd build/
**cmake -DCMAKE_INSTALL_PREFIX=/usr/share/apps ../**
make
sudo make install

But here's the problem. That bolded command gives me this:

-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/brandon/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:9 (find_package)

The problem, I think, is that I cannot cd into "konversation-1.2-alpha6/", but I can cd into '~/konversation-1.2-alpha6", which gives me the above error...

Someone please help, I've been messing with this for three days now.

---

