---
title: "please hepl"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by oblomov on 2009-02-23
i'm trying to install stellarium 0.10 on my hardy distro, but when i type

cmake ../..

this is the output:

CMake Error at cmake/FindQt4.cmake:1276 (MESSAGE):
  The installed Qt version 4.4.0 is too old, at least version 4.4.1 is
  required
Call Stack (most recent call first):
  CMakeLists.txt:78 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
oblomov@oblomov:~/Scrivania/stellarium-0.10.0/builds/unix$



can anyone help me? please...

---

### Post by albinootje on 2009-02-23
> **oblomov said:**
>  The installed Qt version 4.4.0 is too old, at least version 4.4.1 is
  required


Ubuntu Intrepid has the package that you need for compilation :
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libqt4-dev](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libqt4-dev)
Imho it makes sense to compile and run the software on an Ubuntu Intrepid installation.
Because backporting the qt software that you need in Ubuntu Hardy as deb packages might be a lot of work or impossible.

One other option could be to download Qt from the Qt website, and install that in /usr/local/ :
[http://www.qtsoftware.com/downloads/opensource/appdev/linux-x11-cpp](http://www.qtsoftware.com/downloads/opensource/appdev/linux-x11-cpp)

---

### Post by albinootje on 2009-02-23
Because I was curious, I just tried backporting Qt dev files from Intrepid sources on my Hardy system, so i made a start :
> 
$ ~/Desktop/stellarium-0.10.1/builds/unix$ sudo apt-get build-dep libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  doxygen flex libcupsys2-dev libgcrypt11-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev libiodbc2 libiodbc2-dev liblzo2-dev libmysqlclient15-dev
  libopencdk10-dev libreadline5-dev libsqlite3-dev libtasn1-3-dev libxml2-dev libxslt1-dev

$ ~/Desktop/stellarium-0.10.1/builds/unix$ sudo apt-get -b source libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'qt4-x11' packaging is maintained in the 'Svn' version control system at:
svn://svn.debian.org/svn/pkg-kde/trunk/packages/qt4-x11
Need to get 113MB of source archives.
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main qt4-x11 4.4.3-0ubuntu1.2 (dsc) [2506B]
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main qt4-x11 4.4.3-0ubuntu1.2 (tar) [113MB]
8% [2 qt4-x11 9841762/113MB 8%]                                                                                                               844kB/s 2min2s

It looks like this will build Qt 4.4.3 completely.

And I don't know how well Qt 4.3.x and 4.4.3 will live together on one Ubuntu system, but it might work without problems.

---

### Post by Menthu_Rae on 2009-02-25
I'm also interested in this. I'm running Hardy on my EeePC and would like stellarium 0.10.1 so I can use my EeePC when out with my 'scope. :)

I tried using the backports repo but the QT version was still outdated/not high enough for the build... Also, I somehow ended up breaking apt-get and had to re-install (dont ask me how, all I did was close the software-sources app after disabling backports!)...

So yeah, I'll wait for someone to post up proper instructions how to do it under Hardy :)

---

### Post by albinootje on 2009-02-25
> **Menthu_Rae said:**
>  So yeah, I'll wait for someone to post up proper instructions how to do it under Hardy :)

Feel free to backport Qt yourself :
1) add the Ubuntu Intrepid sources to your /etc/apt/sources.list
2) run : sudo apt-get update
3) run : sudo apt-get build-dep libqt4-dev
4) run : sudo apt-get -b source libqt4-dev
5) after successful compilation, look at the produced *.deb files and install them with "sudo dpkg -i"

YMMV.. Compilation might take quite some time (!), I've just started testing this.

---

### Post by albinootje on 2009-02-25
Okay, I've just tested it, and the Qt 4.4.3 debs want to replace the Qt 4.3.x debs, but that also means that all already installed Qt-based applications will be removed!

After that I've ran the following to solve the problem, and go back to the previous state :
> 
sudo aptitude keep-all
-- cut --
Downgrade the following packages:
libqt4-core [4.4.3-0ubuntu1.2 (now) -> 4.3.4-0ubuntu3 (hardy)]
libqt4-gui [4.4.3-0ubuntu1.2 (now) -> 4.3.4-0ubuntu3 (hardy)]
libqt4-qt3support [4.4.3-0ubuntu1.2 (now) -> 4.3.4-0ubuntu3 (hardy)]
libqt4-sql [4.4.3-0ubuntu1.2 (now) -> 4.3.4-0ubuntu3 (hardy)]
qt4-qtconfig [4.4.3-0ubuntu1.2 (now) -> 4.3.4-0ubuntu3 (hardy)]

Score is 857

Accept this solution? [Y/n/q/?] 

After choosing "Y" here, I also had to run this :
> 
dpkg -i --force-all /var/cache/apt/archives/libqt4-*4.3.4*

And then run "sudo aptitude keep-all" again to correct all the Qt version differences problems.

So.. beware, if you have already Qt-based applications installed, then you only want to compile and run this software on an Ubuntu Intrepid installation, or.. compile the Qt 4.4.3 from source (from the Qt website) in Hardy and choose an installation PREFIX like /usr/local

---

