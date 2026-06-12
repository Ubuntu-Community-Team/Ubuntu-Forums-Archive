---
title: "NiVidia GeForce 8400 driver will not install properly"
date: 2009-07-23
forum: Hardware
---

### Post by adam93 on 2009-07-23
Well, like the title says, my NiVidia GeForce 8400 driver will not install properly, and I am using Unbuntu (Jaunty version). I tried to do what one user recommended that worked for another user, which was...

sudo apt-get install envyng-core envyng-gtk envyng-q
tbut, it did not work.
 here's what came up after I did that.
__________________________________________________________________________________


adam@ubuntu:~$ sudo apt-get install envyng-core envyng-gtk envyng-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exiv2 kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data kdepimlibs-data kdepimlibs5 kdesudo khelpcenter4
  libakonadiprivate1 libaudio2 libboost-program-options1.35.0 libclucene0ldbl
  libexiv2-5 libmodplug0c2 libmpcdec3 libmysqlclient15off libphonon4
  libplasma3 libpq5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal1 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x mysql-common phonon phonon-backend-xine python-kde4 python-qt4
  python-qt4-common python-sip4 qt4-qtconfig raptor-utils redland-utils
  soprano-daemon ttf-dejavu ttf-dejavu-extra
Suggested packages:
  kdebase akonadi-server nas libqt4-dev gxine xine-ui libxine1-doc libxine-doc
  libxine1-ffmpeg phonon-backend-vlc phonon-backend-mplayer python-kde4-dbg
  python-qt4-dbg
The following packages will be REMOVED:
  linux-restricted-modules-2.6.28-13-generic
The following NEW packages will be installed:
  envyng-core envyng-gtk envyng-qt exiv2 kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data kdepimlibs5 kdesudo
  khelpcenter4 libakonadiprivate1 libaudio2 libboost-program-options1.35.0
  libclucene0ldbl libexiv2-5 libmodplug0c2 libmpcdec3 libmysqlclient15off
  libphonon4 libplasma3 libpq5 libqt4-assistant libqt4-dbus libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal1 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x mysql-common phonon phonon-backend-xine python-kde4 python-qt4
  python-qt4-common python-sip4 qt4-qtconfig raptor-utils redland-utils
  soprano-daemon ttf-dejavu ttf-dejavu-extra
0 upgraded, 71 newly installed, 1 to remove and 155 not upgraded.
1 not fully installed or removed.
Need to get 72.6MB of archives.
After this operation, 246MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqtcore4 4.5.0-0ubuntu4.1 [1492kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-xml 4.5.0-0ubuntu4.1 [87.4kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-dbus 4.5.0-0ubuntu4.1 [176kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libaudio2 1.9.1-5 [84.1kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqtgui4 4.5.0-0ubuntu4.1 [3590kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libphonon4 4:4.3.1-0ubuntu3 [149kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-script 4.5.0-0ubuntu4.1 [350kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-designer 4.5.0-0ubuntu4.1 [1795kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-network 4.5.0-0ubuntu4.1 [381kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-sql 4.5.0-0ubuntu4.1 [85.6kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-qt3support 4.5.0-0ubuntu4.1 [1034kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-svg 4.5.0-0ubuntu4.1 [129kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libclucene0ldbl 0.9.20-3 [376kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libraptor1 1.4.18-2 [179kB]    
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main mysql-common 5.1.30really5.0.75-0ubuntu10.2 [62.9kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libmysqlclient15off 5.1.30really5.0.75-0ubuntu10.2 [1878kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libpq5 8.3.7-1 [301kB]         
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main librasqal1 0.9.16-1 [108kB]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main librdf0 1.0.8-1 [140kB]        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main soprano-daemon 2.2.2+dfsg.1-1ubuntu1 [138kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libsoprano4 2.2.2+dfsg.1-1ubuntu1 [508kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libexiv2-5 0.18-1ubuntu1 [595kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libstreams0 0.6.4-0ubuntu2 [101kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libstreamanalyzer0 0.6.4-0ubuntu2 [303kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdelibs5-data 4:4.2.2-0ubuntu5 [1989kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdelibs5 4:4.2.2-0ubuntu5 [7066kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdelibs-bin 4:4.2.2-0ubuntu5 [280kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-opengl 4.5.0-0ubuntu4.1 [151kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libmodplug0c2 1:0.8.4-3ubuntu1.1 [173kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libmpcdec3 1.2.2-1build1 [27.0kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libxine1-bin 1.1.16.3-0ubuntu1 [1268kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libxine1-misc-plugins 1.1.16.3-0ubuntu1 [831kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libxcb-shape0 1.1.93-0ubuntu3.1 [5842B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libxcb-shm0 1.1.93-0ubuntu3.1 [5252B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libxcb-xv0 1.1.93-0ubuntu3.1 [9140B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libxine1-x 1.1.16.3-0ubuntu1 [154kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libxine1-console 1.1.16.3-0ubuntu1 [44.8kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libxine1 1.1.16.3-0ubuntu1 [1360B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main phonon-backend-xine 4:4.3.1-0ubuntu3 [169kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main phonon 4:4.3.1-0ubuntu3 [8648B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-webkit 4.5.0-0ubuntu4.1 [3639kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libplasma3 4:4.2.2-0ubuntu5 [611kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-assistant 4.5.0-0ubuntu4.1 [11.6kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-help 4.5.0-0ubuntu4.1 [169kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-sql-mysql 4.5.0-0ubuntu4.1 [23.9kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-test 4.5.0-0ubuntu4.1 [40.9kB]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libqt4-xmlpatterns 4.5.0-0ubuntu4.1 [654kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main qt4-qtconfig 4.5.0-0ubuntu4.1 [80.8kB]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe envyng-core 2.0.1ubuntu1 [119kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe envyng-gtk 1.1.1ubuntu3 [2606B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdebase-runtime-bin-kde4 4:4.2.2-0ubuntu1 [63.7kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdebase-runtime-data-common 4:4.2.2-0ubuntu1 [200kB]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdebase-runtime-data 4:4.2.2-0ubuntu1 [3534kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kde-icons-oxygen 4:4.2.2-0ubuntu1 [15.4MB]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdebase-runtime 4:4.2.2-0ubuntu1 [2055kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libboost-program-options1.35.0 1.35.0-8ubuntu5 [188kB]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libakonadiprivate1 1.1.1-0ubuntu3 [428kB]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdepimlibs-data 4:4.2.2-0ubuntu1 [90.8kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdepimlibs5 4:4.2.2-0ubuntu1 [2510kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-sip4 4.7.9-1ubuntu1 [123kB]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-qt4-common 4.4.4-2ubuntu6 [64.7kB]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-qt4 4.4.4-2ubuntu6 [5695kB]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-kde4 4:4.2.2-0ubuntu2 [5418kB]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main kdesudo 3.4.1-0ubuntu1 [44.3kB]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe envyng-qt 2.0.1ubuntu1 [98.3kB]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main exiv2 0.18-1ubuntu1 [84.5kB]   
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main khelpcenter4 4:4.2.2-0ubuntu1 [1831kB]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main raptor-utils 1.4.18-2 [15.1kB] 
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main redland-utils 1.0.8-1 [62.1kB] 
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main ttf-dejavu-extra 2.28-1 [3092kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main ttf-dejavu 2.28-1 [3104B]      
Fetched 72.6MB in 2min 24s (503kB/s)                                           
Extracting templates from packages: 100%
(Reading database ... 101424 files and directories currently installed.)
Removing linux-restricted-modules-2.6.28-13-generic ...
rmdir: failed to remove `/lib/modules/2.6.28-13-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.28-13-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Cannot find /lib/modules/2.6.28-13-generic
update-initramfs: failed for /boot/initrd.img-2.6.28-13-generic
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
________________________________________________________________________________

So then, a window popped up, and said to use...
"sudo apt-get install - f"

and this is what popped up in the terminal...
___________________________________________

adam@ubuntu:~$ sudo apt-get install - f
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package f

______________________________________________

So, I have absolutely no idea what to do. If you haven't guessed yet, I'm new to Linux, and these forums, so forgive me if I did something wrong,
Can anyone help??

---

