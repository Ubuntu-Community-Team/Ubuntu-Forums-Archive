---
title: "Asus EEE1101HA Graphics Problem"
date: 2010-01-26
forum: Hardware
---

### Post by Kreativ on 2010-01-26
Hi!

After searching for a solution on google and on several forums without being able to fix my problem I've decided to make my own post, so I am sorry if this has been answered before, I was unable to find it with the search function.

I've been trying to do what is instructed in [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
but I can't seem to get it to work. When I install UNR on my new Asus EEE 1101HA it is really choppy which makes using it for anything very hard. Even scrolling on websites takes very long time due to the choppyness.

Since the specifications are
Intel GMA 500 Shared gfx memory (UMA)
I figured that the fix would be the one mentioned in the thread, but so far it hasn't helped at all.

I also tried to run the command which is mentioned later in the thread
> wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh) && sh ./poulsbo.sh
but then it just booted into a terminal which was blinking and I couldn't even write anything.

I had however tried to configure it manually as in the first post before, so that might have influenced the script? I am unsure as this is my first try at running Linux since I once ran Linux Mint on my desktop PC years ago.

Are there any other known fixes, or is this even a known problem for this computer? Or should I try to run the command once again on my fresh UNR install?

Thanks for any answers, and sorry if this should have been in the multimedia section, I thought it fitted better in the Laptop section.

---

### Post by thomi_ch on 2010-02-11
Hi,

Just had the same Problem in Ubuntu Netbook Remix 9.10.. and solved it with this:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic)

I think the poulsbo.sh script is/was updated...

Run's also with latest karmic kernel .19

cheers
thomi

---

### Post by thomi_ch on 2010-02-15
hi all

so, i found now the solution for the GMA500 problem:

First add this ppa to your repos:
[https://launchpad.net/~lucazade/+archive/gma500](https://launchpad.net/~lucazade/+archive/gma500)

then install this packages:
sudo apt-get install psb-kernel-source
sudo apt-get install psb-kernel-headers
sudo apt-get install psb-modules

then read/download/extract/run this one:
[http://poulsbo-karmic.angelfire.com/](http://poulsbo-karmic.angelfire.com/)

what does install.pl:

echo 'deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list
echo 'deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list
echo 'deb [http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu](http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu) jaunty main ' >> /etc/apt/sources.list.d/poulsbo-graphics-alberto-milone.list
echo 'deb-src [http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu](http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu) jaunty main' >> /etc/apt/sources.list.d/poulsbo-graphics-alberto-milone.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F
apt-get update
apt-get install  dkms fakeroot
apt-get install libdrm-poulsbo1
apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware
dpkg -i psb-kernel-*
echo "blacklist i915" >> /etc/modprobe.d/blacklist.conf
update-initramfs -u
cp xorg.conf /etc/X11/xorg.conf

i think the part "dpkg -i psb-kernel-*" in install.pl is not important, then the packages will be installed from lucazade gma500 ppa.


and what's in xorg.conf:
Section "Device"
        Identifier      "GMA500"
        Option "AccelMethod" "EXA"
        Option "DRI" "on"
        Option "MigrationHeuristic" "greedy"
        Option "IgnoreACPI" "yes"
        Driver "psb"
EndSection

Section "DRI"
    Mode    0666
EndSection


Here are information about the system:
ASUS eePC EEE-1101HA
Linux kubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux


More information here:
[http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/](http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/)


Hope this information helps other peoples too, to get the GMA500 up and running quickly :)

cheers and kind regards
thomi

---

### Post by thomi_ch on 2010-02-15
hello

have made changes in the install.pl... you can use this for setting up your Intel GMA 500 grafic, see the attached poulsbo-installation.tar.gz.

mkdir poulspo
cd poulspo
# download the attachment and place it here
tar -zxvf poulsbo-installation.tar.gz
sudo ./install.pl

--- SNIP ---
The content of install.pl is, thanks for original creator:
# read more about adding ppa's on [https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)
# this is the command line way...
sudo add-apt-repository ppa:lucazade/gma500
# now adding some jaunty ppa's, cause there are the packages we need
echo 'deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list
echo 'deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list
echo 'deb [http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu](http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu) jaunty main ' >> /etc/apt/sources.list.d/poulsbo-graphics-alberto-milone.list
echo 'deb-src [http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu](http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu) jaunty main' >> /etc/apt/sources.list.d/poulsbo-graphics-alberto-milone.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F
# updating package list
apt-get update
# installing needed packages
apt-get install dkms fakeroot
apt-get install libdrm-poulsbo1
apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware
# changed by thomi, psb-kernel-* files are from ppa:lucazade/gma500
apt-get install psb-kernel-source psb-kernel-headers psb-modules
echo "blacklist i915" >> /etc/modprobe.d/blacklist.conf
update-initramfs -u
# copying xorg.conf
cp xorg.conf /etc/X11/xorg.conf
--- SNIP ---

after running install.pl run:
sudo reboot


have done that now three times.. every time with success :) :popcorn:

by the way, it works with kernel 2.6.31-19 and 2.6.31-20.. ;)

cheers
thomi

---

### Post by mowglix on 2010-03-27
I've followed the steps above and the resolutions seems to be correct but I can't enable any visual effect. Neither the normal nor the extra. 

Any suggestion for a possible solution?

---

### Post by thomi_ch on 2010-03-29
hello

i don't use effects, and yes.. if i want enable it, they won't work.. don't know if that is adriver issue..

i just found this... maybe this can help:

[http://ubuntuforums.org/showthread.php?p=9022438](http://ubuntuforums.org/showthread.php?p=9022438)

cheers
thomi

---

### Post by nausi on 2010-04-05
[LEFT]the script  works fine. Big thanks
[/LEFT]

---

### Post by thomi_ch on 2010-05-18
hi all GMA500 users.. :)

now upgraded my karmic asus eepc to lucid lynx 10.04... and.. after 1 or two hours i get graphic and wireless runnging..

i allays first install openssh-server and connect from another machine, so it's easier to configur/install/upgrade/reboot the affecting machine.

have found some different solution.. but i think, this one is the easiest way.

a gma500 ppa is born :) thanks for Vitaliy Kulikov ([https://launchpad.net/~slonua](https://launchpad.net/~slonua))
[https://launchpad.net/~gma500/+archive/ppa](https://launchpad.net/~gma500/+archive/ppa)

following steps should bring up the gma500 graphic with the psb driver:

sudo add-apt-repository ppa:gma500/ppa
sudo apt-get update && sudo apt-get ugprade

now remove old packages if you are upgrading from karmic to lucid, if not.. you don't need this step:
sudo apt-get remove psb-firmware psb-kernel-source xpsb-glx xserver-xorg-video-psb libva1 libva poulsbo-config libdrm-poulsbo1
maybe there are some packages, that are not installed.. but.. anyway.. others should be removed before next step.

after that step reboot your system...
sudo reboot

then re-connect (over ssh) to the machine and install the needed psb packages/drivers:
sudo apt-get install psb-firmware psb-kernel-source xpsb-glx xserver-xorg-video-psb libva1 poulsbo-config libdrm-poulsbo1

after that,your xorg.conf will be reconfigured trough poulsbo-config, see install log:
Setting up poulsbo-config (0.1ubuntu2) ...
Modifying xorg.conf through X-Kit...
Done

to check, here is my /etc/X11/xorg.conf, minimal one:
Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite" "Enable"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "psb"
        Option  "ShadowFB"      "True"
EndSection


so.. now it's time to reboot again:
sudo reboot

now? :guitar:  YEAH...

bye the way, i just done above steps while i wrote above steps ;) :popcorn:

now you can check, what psb packages are installed:
sudo dpkg -l | grep psb
ii  psb-firmware                                       0.30-0ubuntu1netbook1ubuntu1                    Binary firmware for the Poulsbo (psb) 3D X11
ii  psb-kernel-source                                  4.42.0-0ubuntu2~1004um2                         Kernel module for the Poulsbo (psb) 2D X11 d
rc  psb-modules                                        4.41.6-0ubuntu1~910um1                          Kernel module built for -generic or -lpia ke
ii  xpsb-glx                                           0.18-0ubuntu1netbook2~1004um1ubuntu1            X11 drivers for Poulsbo (psb) 3D acceleratio
ii  xserver-xorg-video-psb                             0.36.0-0ubuntu3~1004um3ubuntu2                  X.Org X server -- Intel Poulsbo (2D)


sudo dpkg -l | grep libva
ii  libva1                                             0.31.0-1+sds9.1ubuntu1                          Video Acceleration (VA) API for Linux -- run


sudo dpkg -l | grep poulsbo
ii  libdrm-poulsbo1                                    2.3.0-1ubuntu0sarvatt4~1004um1ubuntu1           Userspace interface to kernel DRM services -
ii  poulsbo-config                                     0.1ubuntu2                                      Poulsbo configuration package


about WIRELESS problem... if you are using WICD...
i installed following package, even if wicd or networkmanager is used:
sudo apt-get install linux-backports-modules-wireless-lucid-generic

if you are using wicd as your preferred network manager client, then run following command to get wicd working on lucid:
sudo apt-get remove network-manager network-manager-pptp-gnome network-manager-pptp pptp-linux

i know, above command also removes pptp packages.. but if you're using wicd it's necessary... on my machine it was..

reboot your machine and connect over wicd to your favorite wlan or over cable:
sudo reboot


next step on my asus eepc t91mt is to enable multitouch trough kernel integrated driver/module:
[http://lii-enac.fr/en/projects/shareit/linux.html](http://lii-enac.fr/en/projects/shareit/linux.html)


if you get problem's, just report here.. so we can help

have nive psb'ing...

kind regards from switzerland
thomi

---

