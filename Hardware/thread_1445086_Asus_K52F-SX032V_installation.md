---
title: "Asus K52F-SX032V installation"
date: 2010-04-02
forum: Hardware
---

### Post by rowlandm on 2010-04-02
Hi there,

Thought I would document all the bits and pieces that I learned when trying to install Ubuntu on this Asus K52F-SX032V.

Please keep in mind I was trying to keep mythtv to version 0.21 for my own personal reasons, hence trying the older distributions first.



Asus K52F-SX032V trying to run MythTV 0.21

1/ Tried Jaunty

Installed fine, problems with

- JMicron JMC250 ethernet card picked up jme driver, but could not get DHCP and wouldn't work with Static IP either
- wireless card. Did get working with this "sudo apt-get install linux-backports-modules-jaunty"  [http://ubuntuforums.org/showpost.php?p=7409829&postcount=2](http://ubuntuforums.org/showpost.php?p=7409829&postcount=2)
- vesa screen for Xorg, only 1024x768


2/ So tried Linux Mint 8 and Karmic Koala

Could not install at all

- Problem with laptop monitor going blank with a backlit screen during boot up. Tried  i915.modeset=0 workaround but screen eventually blanked out again. Apparently you can plugin a second monitor and that is the other workaround.

3/ So tried Lucid Lynx Beta

- Installed fine and picked up ethernet and wireless out of the box
- Haven't checked the resolution but I am sure it is fine
- Installed MythTV 0.21 front end (see below)


Setup MythTV 0.21 front end for Lucid Lynx

1) sudo gedit /etc/apt/sources.list

#added
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse



2) sudo gedit /etc/apt/preferences 

# created brand new file
# pinning mythtv to stay at v0.21 for compatibility with backend
Package: mythtv
Pin: version 0.21*
Pin-priority: 1001

Package: mythtv-common
Pin: version 0.21*
Pin-priority: 1001

Package: mythtv-frontend
Pin: version 0.21*
Pin-priority: 1001

3) sudo apt-get update

4) Download and install this package manually (ie dpkg -i *.deb or open in debi program and install ) as it must be located somewhere else in Jaunty

[http://packages.ubuntu.com/jaunty/libraw1394-8](http://packages.ubuntu.com/jaunty/libraw1394-8)

5) sudo apt-get install mythtv-frontend

6) Setup mythtv frontend - worked perfectly, sound and everything!

Thanks very much to the two posts below that helped me set this up!

[http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html](http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html)

[http://ubuntuforums.org/showpost.php?p=8380319&postcount=3](http://ubuntuforums.org/showpost.php?p=8380319&postcount=3)

---

