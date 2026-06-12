---
title: "No sound on my laptop Compaq CQ 510 using Ubuntu 9.04"
date: 2009-11-19
forum: Hardware
---

### Post by saikat_tapu on 2009-11-19
[FONT=Book Antiqua][SIZE=5][COLOR=Blue]i m able to see video but do not get any audio in my hp compaq 510 laptop.

not finding any solution...

please help me out of this....
[/COLOR][/SIZE][/FONT]

---

### Post by shababhsiddique on 2010-03-04
bump

same problem here... maybe a problem with soundcard driver.... no player workd...

---

### Post by akand074 on 2010-03-04
Have you tried going to the sound preferences (you can just right click on the sound icon and click preferences I believe), it could be the volumes are low, or the wrong settings are selected. Also pulse audio is used by default you can try switching to the Alsa drivers which I personally have found to be better. Unfortunately I'm not booted into ubuntu right now so that is the best help I can be:(

---

### Post by shababhsiddique on 2010-03-04
bump. . . . having same problem. CQ510 jaunty..... worked fine in 8.10

---

### Post by shababhsiddique on 2010-03-04
> **akand074 said:**
> Have you tried going to the sound preferences (you can just right click on the sound icon and click preferences I believe), it could be the volumes are low, or the wrong settings are selected. Also pulse audio is used by default you can try switching to the Alsa drivers which I personally have found to be better. Unfortunately I'm not booted into ubuntu right now so that is the best help I can be:(

not that easy...

theres been a bug report. [https://bugs.launchpad.net/ubuntu/+bug/414770/](https://bugs.launchpad.net/ubuntu/+bug/414770/)


my settings are fine, front ,headphone master all set to 80% and not mute!....

HDAintel is showed...plz read the bug report and help..



by the way . . how do I upgrade ALSA to latest version?

---

### Post by shababhsiddique on 2010-03-05
> **saikat_tapu said:**
> [FONT=Book Antiqua][SIZE=5][COLOR=Blue]i m able to see video but do not get any audio in my hp compaq 510 laptop.

not finding any solution...

please help me out of this....
[/COLOR][/SIZE][/FONT]hey buddy


i think I have got a solution
worked for me....same compaq510 with jaunty



To do this, we must begin by determining our version of alsa as follows :

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

To avoid problems during the upgrade of Alsa-utils, we need to stop it with the following command :

sudo /etc/init.d/alsa-utils stop
We must then install the necessary tools to compile along with the kernel headers :

sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

Then, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils :

cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)

After that, we create a new folder for the compilation and installation of the 3 files. Then, we move the 3 tar files that we just downloaded in this folder :

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

Unpack the 3 tar files :

sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

We compile and install alsa-driver :

cd alsa-driver*
sudo ./configure
sudo make
sudo make install

We compile and install alsa-lib :

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

We compile and install alsa-utils :

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

Then, we remove the 3 tar files in our personal folder that are not anymore necessary :

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

Then, just restart your computer and your alsa version should be 1.0.20!

You can verify that you have now indeed have this version of alsa :

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on May 9 2009 for kernel 2.6.28-11-generic (SMP).

Just to be sure everything is well configured, execute this command :

sudo alsaconf

---

