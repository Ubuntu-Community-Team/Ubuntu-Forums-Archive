---
title: "GeForce 8400gs + Jaunty +Nvidia driver 180"
date: 2009-04-25
forum: Hardware
---

### Post by iKevin on 2009-04-25
Hi All

I installed jaunty and prior to doing so I looked at which nvidia drivers where available.  I noticed that nvidia version 180 was available, which was the same driver that I was using in intrepid without trouble.  So, I went ahead and installed.  The restricted driver tool popped up and recommended 180 again and I installed that driver.  Upon rebooting, X failed to start.  Here is the error from the log file.  

Is there generally an issue with the nvidia drivers and jaunty?  I find it odd that it proposed the same driver that worked with intrepid yet it failed.

  

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

---

### Post by iKevin on 2009-04-25
OK, I am a novice but I solved this by blind stupid luck.  I was doing more googling and I found that some have had a conflict between my TV Tuner, which uses the cx18 module, and the nvidia drivers.  Apparenty, the cx18 module is really buggy.  Anyways, blacklisting that module fixed the issue.

---

### Post by r3ad3r on 2009-04-25
Hi guys, I had this same problem, but I manuanly reinstall apt-get install nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-libvdpau-dev nvidia-180-modaliases
After reboot, nothing happends, but another reboot was ok.Now I would like to know, how to change resolution on my laptop Acer aspire 5920G with this graphic card, because this default resolution isn`t very well, can you help me guys with that please?

---

### Post by PomTom on 2009-04-25
> **iKevin said:**
> 

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Same problem here with a GeForce Go 7600. Just upgraded from 8.10 to 9.04.

---

### Post by iKevin on 2009-04-25
> **PomTom said:**
> Same problem here with a GeForce Go 7600. Just upgraded from 8.10 to 9.04.

Do you happen to have a TV-tuner based on CX23418?  I have a Hauppauge HVR-1600 which needs the cx18 module.  I blacklisted this module and that fixed the problem.  From everything that I read using google, cx18 is not really ready.  It should be blacklisted as the default.

---

### Post by futuroimperfetto on 2009-05-02
Hello,

 same problem here on a Dell XPS m1330 with a GeForce 8400 GS. I don´t have my laptop connected to any TV-tuner, but maybe I do have installed this cx18 module. How do I blacklist it (or should I just uninstall it via terminal)?

I also tried to install the 180 driver from terminal but it wouldn't work even after a few reboots. When I have the 180 driver installed the only thing I can do is tell the system to go back to its generic default configuration (aka using no nvidia driver).

Right now am using the 173 driver without issues, but they call it "basic driver" so I'd like to see 180 working.

Thanks!

---

### Post by amor0fati on 2009-05-04
I can't seem to get drivers of any version to even activate (stalls out or something), and I'm stuck in low-graphics mode.

---

### Post by ugga on 2009-05-11
I have the same problem with NVIDIA 8400m G. ;(

---

### Post by Almighty on 2009-05-11
I get that too. 

log into a root console

```
 sudo /etc/init.d/gdm stop
```

```
 sudo sh ./NVIDIA-Linux-x86-185.18.08-pkg1.run --uninstall 
```

reboot and you should be good

---

### Post by Toast2120 on 2009-05-11
> **PomTom said:**
> Same problem here with a GeForce Go 7600. Just upgraded from 8.10 to 9.04.

Hey all. Have 8800 GTS SLI with AMD 4200 (64bit) on da Jakalope and had similar problems. It says something about "No recent image found"

Anyway the code that Almighty posted
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-185.18.08-pkg1.run --uninstall

Would that work on my system to get it working?
Also, whats the best way to install video drivers? Terminal or the "Hardware drivers" fix under System -> Admin?

---

### Post by amor0fati on 2009-05-11
My problem was that Jaunty wasn't on my menu.lst, so I added it and installed the drivers with envyng.

---

### Post by Almighty on 2009-05-12
> **Toast2120 said:**
> Hey all. Have 8800 GTS SLI with AMD 4200 (64bit) on da Jakalope and had similar problems. It says something about "No recent image found"

Anyway the code that Almighty posted
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-185.18.08-pkg1.run --uninstall

Would that work on my system to get it working?
Also, whats the best way to install video drivers? Terminal or the "Hardware drivers" fix under System -> Admin?


What I posted will remove the driver that you installed and should restore your system to its previous state. It should have been backed up when you installed the driver.

And the best way to install video drivers? Well, I would think that's pretty subjective. The most popular way would be either the hardware drivers app thru Ubuntu or Envyng.

---

### Post by Gausian on 2009-05-12
A general rule of thumb is when installing or upgrading, its wise to run update manager and get all updates before trying to install restricted drivers.

Ive never had any problems as long as i installed all updates before the drivers.

---

### Post by Jeconti on 2009-06-19
What driver do you use for the HVR-1600 if you blacklisted the cx18?

---

### Post by carcar1 on 2009-06-19
really guys/girls?  use envy automated install of drivers and does all the work for you.

```
sudo apt-get install envyng-core envyng-gtk envyng-qt
```

I have the 8400gs works fine with compiz settings all turned up!  I am using the kernel for karmic or 9.10 which is with the -13 at the end.  (not promoting use)  I use Ultimate Edition 2.2 came out yesterday

---

### Post by adam93 on 2009-07-23
I tried to do what carcar1 said, and this is what happened... (new to linux by the way)

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

---

### Post by mozzwald on 2009-07-23
adam93:

try this instead:

```
sudo apt-get install envyng-core envyng-gtk
```It appears you are running unbuntu which uses gtk by default and not qt (used by Kubuntu). Not sure if that could have caused the error, but it's worth a shot.

Edit:
Apparently there isn't a gtk version as of yet so ignore this. Sorry.

---

### Post by adam93 on 2009-07-23
Thanks for the help! =]
I tried that, and this is what popped up:


adam@ubuntu:~$ sudo apt-get install envyng-core envyng-gtk
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-restricted-modules-2.6.28-13-generic
The following NEW packages will be installed:
  envyng-core envyng-gtk
0 upgraded, 2 newly installed, 1 to remove and 155 not upgraded.
1 not fully installed or removed.
Need to get 0B/122kB of archives.
After this operation, 1872kB disk space will be freed.
Do you want to continue [Y/n]? Y
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

---

### Post by adam93 on 2009-08-21
I worked it out!
woot.

---

### Post by soulglo83 on 2009-11-30
> **iKevin said:**
> OK, I am a novice but I solved this by blind stupid luck.  I was doing more googling and I found that some have had a conflict between my TV Tuner, which uses the cx18 module, and the nvidia drivers.  Apparenty, the cx18 module is really buggy.  Anyways, blacklisting that module fixed the issue.

Totally worked for me. Sucks to live w/o tuner card, but it's the only real solution to this problem until cx18 is a bit more mature.

Many thanks iKevin, after staying awake until midnight local time on a work night, im very grateful to finally stick a fork in this bloody thing and get to bed:p

---

### Post by betojf on 2010-03-21
There is a better way.:p  

Step by step at bottom, after (********)

So I have An HVR-1600 and a GeForce 8400GS....

After researching the issue, I've found that this is a simple error as documented 

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Driver_refuses_to_load_with_mysterious_errors](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Driver_refuses_to_load_with_mysterious_errors)

and 

[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small#grub](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small#grub)

The error lies in the virtual memory. As I understand this, there is not enough memory and one card (HVR-1600) wins.

The solution is to edit the menu.lst file under /boot/grub and look for a line that looks similar to the line below: 

kopt=root=UUID=1029384-7e40-ffd2-9968-7a8b9e78f9g7s ro

edit line, so that after ro you will have something like below:

kopt=root=UUID=1029384-7e40-ffd2-9968-7a8b9e78f9g7s ro vmalloc=192M

*********************************
Step by step:
Breathe, concentrate, pay attention:

In a terminal window or Konsole:

```
sudo pico /boot/grub/menu.lst
```Once inside of the file, search for a line that looks like this (the UUID information will be different):

```
kopt=root=UUID=1029384-7e40-ffd2-9968-7a8b9e78f9g7s ro
```right before "ro", put vmalloc=192M, so that the line looks like:

```
kopt=root=UUID=1029384-7e40-ffd2-9968-7a8b9e78f9g7s ro vmalloc=192M
```Then, hit CTRL+O and ENTER, and then CTRL+X. This will bring you back to the terminal. At this point, we need the startup system to reconfigure itself, so we type the following command

```
sudo update-grub
```

You can try 256M instead of 192M if you want, but it may not work.

What we've done is create an automatically booting procedure that will  allocate more Virtual memory to the video cards.

Sources:

[http://ubuntuforums.org/showthread.php?t=1009612](http://ubuntuforums.org/showthread.php?t=1009612)
[http://ubuntuforums.org/showthread.php?t=1136766](http://ubuntuforums.org/showthread.php?t=1136766)
[http://ubuntuforums.org/showthread.php?t=1002287](http://ubuntuforums.org/showthread.php?t=1002287)
[http://www.gossamer-threads.com/lists/mythtv/users/339072](http://www.gossamer-threads.com/lists/mythtv/users/339072)
[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small#grub](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small#grub)

---

