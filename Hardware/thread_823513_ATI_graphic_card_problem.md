---
title: "ATI graphic card problem"
date: 2008-06-09
forum: Hardware
---

### Post by mdaryabe on 2008-06-09
Hey,
Im a complete newbie to Linux, while back i got the ubuntu 7.10 and installed on my pc(Dual Boot with Vista) and at that time i had difficulty installing my graphic card drivers so i kind of gave up on it. then couple of days ago my friend told me that 8.04 is released and when i checked ATI website there was a new driver available for HD3XXX series, so i decided to install the 8.04, first i upgraded the 7.10 i had then followed every single tutorial about installing the ATI drivers and no luck, i thought i messed up the OS itself, so i decided to reformat and reinstall the Ubuntu 8.04 from zero.

when for the first time ubuntu loaded, the resolution was at 1280X1024, then i followed this instruction how to install the driver, and i was back to square one, stock at 800X600 resolution, graphic card not detected and when i go to check the restricted drivers, there is nothing there.

Is it possible someone could help me with this, to basically install the Driver for ATI HD3870 X2, on Ubuntu 8.04. is it the problem with X2 part, maybe ubuntu(linux in general) dont handle dual GPU yet or something ?!


Link of all the tutorials I followed:
[https://a248.e.akamai.net/f/674/9206...at85-inst.html](https://a248.e.akamai.net/f/674/9206...at85-inst.html)
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

There were couple of other ones which i lost the links after 3 days of going back an forth between them.

Appreciate any help.

---

### Post by mdaryabe on 2008-06-09
any hope ?

btw correct links are :
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat85-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat85-inst.html)

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (both methods)

---

### Post by timcredible on 2008-06-09
did you do system->administration->hardware drivers to install your ati drivers?  if not, try re-installing and do that.  if you already did that, then you'll need to do some searching to get the drivers to work - personally, i wouldn't work that hard, i would try another distro or just wait until the next ubuntu comes out and see if it's got a driver for your system.

---

### Post by mdaryabe on 2008-06-09
yeah tried those,
but do you know generally if there is any problem with dual ATI GPU  cards with ubuntu ?

---

### Post by mdaryabe on 2008-06-10
Ok here is what happen:

> sudo apt-get update 

Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy Release.gpg     
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/main Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/restricted Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/universe Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates Release.gpg
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security Release.gpg
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy Release
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates Release
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security Release
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/main Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/restricted Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/restricted Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/main Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/multiverse Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/universe Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/universe Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy/multiverse Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/main Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/main Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/universe Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/universe Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/main Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/restricted Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/restricted Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/main Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/universe Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/universe Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-security/multiverse Packages
Reading package lists... Done

> sudo apt-get install linux-restricted-modules-generic restricted-manager

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.3.3-0ubuntu8
You should explicitly select one to install.
E: Package restricted-manager has no installation candidate

> sudo apt-get install xorg-driver-fglrx

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx-amdcccle-envy fglrx-control-envy xorg-driver-fglrx-dev-envy
  xorg-driver-fglrx-envy
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 4 to remove and 3 not upgraded.
Need to get 9951kB of archives.
After this operation, 10.6MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com]("http://archive.ubuntu.com") hardy-updates/restricted xorg-driver-fglrx 1:7.1.0-8-3+2.6.24.13-18.41 [9951kB]
Fetched 9951kB in 11s (850kB/s)                                                
(Reading database ... 149868 files and directories currently installed.)
Removing fglrx-amdcccle-envy ...
Removing fglrx-control-envy ...
Removing xorg-driver-fglrx-dev-envy ...
Removing xorg-driver-fglrx-envy ...
 * Stopping atieventsd                                                   [ OK ] 
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 149793 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.13-18.41_i386.deb) ...
Setting up xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.13-18.41) ...
Installing new version of config file /etc/ati/signature ...
 * Starting atieventsd                                                   [ OK ]

> sudo depmod -a

4-5 sec pause and then next line


doesnt let me to edit it, but Driver "fglrx" been added before. doubled checked with pico.
> sudo gedit /etc/X11/xorg.conf

No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

> sudo aticonfig --initial -f

No protocol specified
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
 Load  "glx"
        Load  "GLcore"
        Load  "v4l"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

also at this point computer doesnt run any other software nor let me restart it throu GUI.


Any new hope ?

---

