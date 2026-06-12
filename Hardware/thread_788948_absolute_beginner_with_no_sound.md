---
title: "absolute beginner with no sound"
date: 2008-05-10
forum: Hardware
---

### Post by bradleyporter on 2008-05-10
Hi I am a complete beginner (and technophobic) and can't seem to figure out why I have no sound since I installed Ubuntu. I use a Fujitsu Siemens Amilo M1450G latop. 
Can anyone help. 
By the way I did go to [http://ubuntuforums.org/showthread.php?t=759338&highlight=sound&page=2](http://ubuntuforums.org/showthread.php?t=759338&highlight=sound&page=2) for help but it hasn't worked.

---

### Post by Yellow Pasque on 2008-05-10
You can try OSS 4.1 if all else fails
```
sudo /etc/init.d/alsa-utils stop
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0

sudo apt-get -y install linux-headers-`uname -r` build-essential gawk libtool libgtk2.0-dev libesd0 esound esound-common linux-sound-base gcc-multilib libesd0-dev mercurial libssl0.9.8 libssl-dev
cd /usr/src
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss41build
cd oss41build/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```
[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

