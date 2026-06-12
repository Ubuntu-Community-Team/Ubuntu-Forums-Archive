---
title: "Kubuntu on HP/Compaq V2000Z"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by zxg32 on 2006-02-01
The following are my notes on installing and using 64-bit kubuntu on V2000Z. Hope my experience may be helpful to you.


Installation:
1. download kubuntu-5.10-dvd-amd64.iso and burn dvd
2. boot dvd, type "expert noapic" at prompt
3. "expert" mode will enable root account and ask for root password
4. "noapic" parameter is necessary, otherwise it will hang at line
input: AT Translated Set 2 keyboard on isa0060/serio0
5. try remove "splash" parameter to boot into CLI if X11 hangs at line
Checking battery state...
6. prepare build environment, use dselect to install packages such as
gcc-3.4, linux-headers-amd64-k8, linux-source-2.6.12, linux-tree


Sudo:
1. sudo does not work after installation, no matter what password -
root or user - is inputted, sudo reports error "broken pipe"
2. administrator mode in GUI programs that require sudo does not work
either, the message is "conversation with su failed"
3. this is a much-complained-about bug in (k)ubuntu, installation fails
to add non-root username to /etc/sudoers
4. suppose non-root username is mike, login as mike, then run su to
become root, and run visudo to edit following lines in /etc/sudoers
# root ALL=(ALL) ALL
mike ALL=(ALL) ALL
5. run "sudo passwd -l root" to disable root account, but see ubuntu
bug #28551 for more details


ATI driver:
1. boot into CLI, startx fails after installation
2. read [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
3. download ati-driver-installer-8.20.8-x86_64.run, which has TUI and GUI
4. don't run it now, or it reports error in /usr/share/fglrx/fglrx-install.log
AGPGART module build failed with return value 2
[Error] Kernel Module : Failed to install compiled kernel module
5. install from repository first, current version is 6.8.0-8.8.25-0ubuntu11.1
sudo apt-get install xorg-driver-fglrx
6. echo fglrx | sudo tee -a /etc/modules
7. sudo apt-get install linux-restricted-modules-$(uname -r)
8. edit /etc/X11/xorg.conf to
replace Driver "ati" with Driver "fglrx"
comment out or delete Load "int10"
9. restart computer, it should boot into X11 GUI
10 it's not over yet, compiling mplayer gives error
/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL
11 still need ATI proprietary driver, however don't run installer directly, it
will say "installation complete", which is misleading because log file has
the same error, the script loaded X.org driver, thought it was ATI driver
and reported success, but that's not the case
12 remove X.org driver
sudo remove xorg-driver-fglrx; sudo dpkg --purge xorg-driver-fglrx
13 enable universe repository, i.e. uncomment following lines in /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
14 sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
15 fakeroot ./ati-driver-installer-8.20.8-x86_64.run --buildpkg Ubuntu/breezy
16 sudo dpkg -i *.deb
17 sudo module-assistant build,install fglrx-kernel
18 go to [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198) and download the
work-around libdri.a, backup the existing one and replace it
19 reboot, try fglrxinfo and fgl_glxgears to verify ATI driver is up
20 edit following lines in /etc/X11/xorg.conf, virtual screen does not work
Depth 24
Modes "1280x768" "1024x768" "800x600" "640x480"
# Virtual 1280 1280
21 fireglcontrolpanel does not work because it's 32-bit, it's not indispensable,
but read on to build a 64-bit one
22 gunzip and untar /usr/src/ATI/fglrx_panel_sources.tgz
23 sudo cp /usr/lib/libGL.so.1.2 /usr/X11R6/lib/
24 sudo apt-get install libqt3-mt-dev libxxf86misc-dev libxxf86vm-dev
25 touch fglrx_pp_proto.h; chmod u+w *
26 echo '#include <qstylefactory.h>' >> FireGLControl.h
27 edit following lines in main.cpp
//QApplication::setStyle ( new QWindowsStyle ) ;
QApplication a( argc, argv );
a.setStyle( QStyleFactory::create("windows") );
28 env QTDIR=/usr/share/qt3 make


Ethernet, USB, CD/DVD:
1. no special treatment needed, works automatically after installation
2. lspci recognizes it


Wireless:
1. sudo apt-get install ndiswrapper-utils
2. visit [http://ndiswrapper.sourceforge.net/m...index.php/List](http://ndiswrapper.sourceforge.net/m...index.php/List)
3. locate V2000Z and download its Windows XP x64 driver, unzip it
4. sudo ndiswrapper -i bcmwl5.inf
5. sudo ndiswrapper -m
6. echo ndiswrapper | sudo tee -a /etc/modules
7. edit /etc/network/interfaces, restart to use wireless instead of ethernet
# map eth0
map wlan0
# iface eth0 inet dhcp
iface wlan0 inet dhcp


Touchpad:
1. edit following lines under synaptics section of /etc/X11/xorg.conf
# Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
2. synclient -l


Firefox:
1. install 32-bit version for the sake of plugin compatibility
2. install latest version from mozilla.org, not apt-get repository
3. follow [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)
4. flash has no sound when artsd running, artsdsp does not help, to work around
System Settings -> Sound & Multimedia -> Auto-suspend if idle 2 seconds
5. type following commands to see app & lib binaries are 32-bit
file /usr/local/firefox32/firefox-bin
ldd /usr/local/firefox32/firefox-bin
6. 64-bit and 32-bit binaries are incompatible, that is, 64-bit apps
require 64-bit libs and 32-bit apps require 32-bit libs
7. alsa drivers are 64-bit, but they are built into the kernel as modules and
kernel has 32-bit code interface, that's why 32-bit flash plugin can play
audio when no sound binaries are under /lib32, /usr/lib32, /usr/X11R6/lib32


MPlayer:
1. download and untar latest mplayer source, skin, and font
2. sudo apt-get install manpages-dev autoconf automake
3. sudo apt-get install flex bison g++ gcc-doc x-window-system-dev
4. sudo apt-get install libtool libgtk1.2-dev libpng-dev libartsc0-dev
5. libartsc0-dev is crucial, it contains artsc-config that mplayer
uses to detect and build support for KDE aRts
6. ./configure --enable-gui; make; sudo make install
7. sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/
sudo chmod a+r /usr/local/share/mplayer/Skin/default/*
8. sudo cp -r gb2312/* /usr/local/share/mplayer/font/
sudo chmod a+r /usr/local/share/mplayer/font/*
9. echo 'dev.rtc.max-user-freq=1024' | sudo tee -a /etc/sysctl.conf
10 gmplayer -prefer-ipv4
11 mplayer is 64-bit and integrates many common codecs except realmedia and
quicktime audio, whose codecs are currently only 32-bit and non-open source
12 mplayer source can be compiled as 32-bit by dchroot, but it requires
a lot of 32-bit libs and tools, really cumbersome to do


KDE:
1. Regional & Accessibility -> Keyboard Layout -> Xkb Options
-> Third level choosers -> Press any of Win-keys to choose 3rd level
2. Regional & Accessibility -> Keyboard Shortcuts -> Global Shortcuts
-> Panel -> Popup Launch Menu -> press Win-key, it shows ISO_Level3_Shift
3. echo '#\! /bin/sh\nkmix' > ~/.kde/Autostart/kmix
4. chmod a+x ~/.kde/Autostart/kmix
5. KDE Menu Editor -> System -> Konsole -> Command "konsole --ls"
6. alias ls ls --color
7. alias spell 'grep \!* /usr/share/dict/american-english'
8. alias traceroute 'echo try tcptraceroute\!; /usr/bin/traceroute'


Firewall:
1. sudo apt-get install firestarter
2. echo '#\! /bin/sh\nsudo firestarter --start-hidden' > ~/.kde/Autostart/firestarter
3. chmod a+x ~/.kde/Autostart/firestarter
4. suppose non-root username is mike, run "sudo visudo" to add following line
mike ALL=NOPASSWD:/usr/sbin/firestarter
5. System Settings -> User Account -> Session Manager -> Start with an empty session


MLDonkey:
1. sudo apt-get install mldonkey-server kmldonkey
2. add port 6881-6889 and 4662-4672 to firestarter inbound traffic policy


Swap file:
1. sudo dd if=/dev/zero of=/swapfile bs=1024 count=524288
2. sudo mkswap /swapfile
3. sudo swapon /swapfile
4. add the following line to /etc/fstab
/swapfile swap swap defaults 0 0
5. cat /proc/swaps; echo; echo; free -t


Grub:
1. remove unnecessary and redundant lines in /boot/grub/menu.lst
2. change default value, starting from 0, in /boot/grub/menu.lst
3. keep or delete "splash" and "quiet" boot parameter, e.g.
/boot/vmlinuz-2.6.12-10-amd64-k8 root=/dev/hda3 ro noapic quiet

---

### Post by sithia on 2006-02-10
My laptop is different but I followed your ATI install path. I'd tried two others already this week. I couldn't believe my eyes when it worked for me. THANK YOU!

---

