---
title: "how to install softwares"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by ved34957 on 2009-02-02
i have downloaded mplayer,kmplayerand vlcplayer for ubuntu. but unable to install them on ubuntu.how to solve this problem?

---

### Post by howefield on 2009-02-02
Where have you downloaded them from and what are the file names ?

The easy way is to add the medibuntu repository and use Synaptic Package Manager to install the programs.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by x33a on 2009-02-02
most likely you have downloaded tar.gz files.

these contain the source code of the software and you have to compile to install the software. compilation can be a bit over the head for new users. so install them from the official repositories, or download .deb files which can be installed by double clicking like .exe files.

for more info:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

for latest vlc debs: [http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

for latest mplayer and smplayer, add this to your sources:

[http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) intrepid main

---

### Post by acidboot3r on 2009-02-02
You shouldn't really lower yourself down to getting tar.gz files unless you know that there are no .deb files (ubuntu version of the windows .exe)

You should check Add/Remove Programs in the Applications menu and search for your programs there.

---

