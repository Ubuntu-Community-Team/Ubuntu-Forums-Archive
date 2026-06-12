---
title: "libqt4-webkit"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by baderd on 2009-05-16
Hey Folks,

   I have a problem with a broken package. I used the Update Manager to migrate from 8.04LTS to 9.04LTS and other than botching up my Xorg video drivers that went pretty well. A few weeks past and I was using the Update Manager to keep my system up to date, when....I got a broken package.

libQt4-webkit failed to update with the following error message...

E: /var/cache/apt/archives/libqt4-webkit_4.5.0-0ubuntu4.1_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtWebKit.so.4.5.0')

uname -a yields the following, and I'm actually running a 64 bit AMD quad core system.
Linux MySys 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

So...? I got no clue here. should I download the source files and try to build it myself? Since so much other stuff depends on libQt4 I'm pretty broken here, for example I can't install Adobe's flash plugin for Firefox. 

Thanks for any help/ pointers etc., -Dan

---

### Post by baderd on 2009-05-16
Ok, it's true I'm an idiot and lack some of the more basic skills of apt-get. ):P

solved the problem with 

sudo apt-get clean
sudo apt-get -f install

But why wouldn't the GUI called "Update Manager" do the same thing when I ask it to try installing/fixing a broken package?

---

