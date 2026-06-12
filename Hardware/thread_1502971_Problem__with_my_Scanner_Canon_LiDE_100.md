---
title: "Problem  with my Scanner Canon LiDE 100"
date: 2010-06-06
forum: Hardware
---

### Post by mohameds102004 on 2010-06-06
hello

i have bought my new scanner Canon LiDE 100 and i cant found it 

using Xsane .. how i could install it's driver !! PLZ help me :(

---

### Post by ajgreeny on 2010-06-06
Everything I can find suggests that you will not get this scanner to work at all in any linux distro.  Canon are notoriously bad at supporting linux with drivers for any of their machines.  Some printers can be made to work, but many can not, and scanners are even worse.

See if you can change it for something else where you bought it, but before you do check in the ubuntu hardware support wiki for good machines which will work.
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by desertdog on 2010-06-14
Support has recently been added for this scanner. You have to download the latest source code and compile. Below is instructions copied from a Shutter4U post

```
To get this working, here are the steps to take:

1) You need some usb libraries, so, in a terminal type:

sudo apt-get install libusb-dev build-essential libsane-dev

2) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

sudo apt-get install git-core

3) Now use the git that was just installed to get the sane backends using the following command:

git clone git://git.debian.org/sane/sane-backends.git

That downloads the backends and puts them in a folder called sane-backends in your home folder.

4) Change directory into the new sane-backends folder and compile them:

cd sane-backends

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

make <--- this one takes a while

sudo make install

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions.

5) You need to edit a file, but you need to be root to edit it, so:

sudo gedit /lib/udev/rules.d/40-libsane.rules

and add the following 2 lines:

# Canon CanoScan Lide 100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY! 
```

---

### Post by pt123 on 2011-01-01
or just use this PPA to avoid compiling

[http://ubuntuforums.org/showthread.php?p=9462309#post9462309](http://ubuntuforums.org/showthread.php?p=9462309#post9462309)

---

### Post by kgary on 2011-01-03
I followed the instructions to manually compile the backend for the canon lide 100 scanner. I did run into a few problems. I had to create a scanner group, and check off each user account for the group, then authenicate with my password; before the scanner would work. I also had to reboot the machine.
 
At last my Canon LiDE 100 scanner is working! I just have one problem left. The unit seems to make a lot more noise scanning, then what it does on a Windows machine. The scanner growls; but it does work! I am reluctant to use the scanner now, because of the noise.

---

### Post by pt123 on 2011-01-11
you should contact the sane developer as the driver for this was recently worked upon
[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON)

[http://www.sane-project.org/mailing-lists.html](http://www.sane-project.org/mailing-lists.html)

---

