---
title: "Logitech webcam"
date: 2008-05-10
forum: Hardware
---

### Post by styleruk on 2008-05-10
Hi

Now I know there is a ton of information regarding web cams here and I think I've read them all and spent more time than it is worth trying to set the camera up, however, although I get an image it is very dark and out of focus and unusable.  I paused over the buy now button when I gave up last night and thought I'd buy a new one, then I thought.....no!  I'm not giving up.

spca5xx

Apparently, this is a driver that will sort it out.  I'm having trouble installing it though, can anyone help me please.

This is the readme for this driver;

[COLOR="Blue"]
[SIZE="2"][SIZE="3"][SIZE="2"]This package provides the gspca source code that can be used to build
modules that work with your custom built linux kernel. The source files are
located in /usr/src/gspca-source.tar.bz2; unpacking that file in /usr/src will
produce a build tree in /usr/src/modules/gspca/ (The tar file can also be
unpacked elsewhere).

Building gspca kernel modules with module-assistant
===================================================

Please install the module-assistant package and issue the following commands
in a shell:-

  $ m-a prepare
  $ m-a a-i gspca

m-a is short for module-assistant, and a-i is short for auto-install. Please
see the module-assistant documentation for futher details about this process.

For full details of gspca please visit [http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html)

If you need information on the Debian packaging team please visit
[http://alioth.debian.org/projects/pkg-spca5xx/](http://alioth.debian.org/projects/pkg-spca5xx/)[/SIZE][/SIZE][/SIZE][/COLOR]

Now, I've tried to install this and even found a step-by-step newbie way of doing it on the many forums I've trawled but I get this error;

root@simon-desktop:/home/simon# m-a prepare
Getting source for kernel version: 2.6.24-16-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Done!
root@simon-desktop:/home/simon# m-a a-i gspca

Updated infos about 1 packages
Getting source for kernel version: 2.6.24-16-generic


I'm using Ubuntu 8.04.


Thank you in advance 

Simon

---

### Post by vyruss on 2008-05-16
My logitech webcam uses the spca driver included in ubuntu 8.04 and worked in a fresh install without my having to install anything by hand. Just try tinkering with your contrast/brightness/color/whatever options the program you're using for your webcam has.

Now the out of focus part, try using the focus wheel around your webcam's lens. Spinning it around focuses your camera.

---

### Post by balagosa on 2008-05-17
> **styleruk said:**
> 
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Simon

is there by any chance that you are running Synaptic Package Manager OR Add/Remove Applications while doing a ```
root@simon-desktop:/home/simon# m-a prepare
``` at terminal?

---

### Post by styleruk on 2008-05-18
I tried again with nothing else running just to check and still the same issue.
I've tried rotating the focus bezel with no result in picture.  When I say it's out of focus, I mean it's miles out of focus.

---

### Post by vyruss on 2008-05-19
> **styleruk said:**
> I tried again with nothing else running just to check and still the same issue.
I've tried rotating the focus bezel with no result in picture.  When I say it's out of focus, I mean it's miles out of focus.

Maybe your webcam is defective? I've never heard of drivers throwing a webcam out of focus :/

Also you could try the driver installation using sudo instead of a root account?

---

### Post by WTF_Shelley on 2008-09-30
if the webcams blurry, have you tried cleaning the lens?  Silly thing to ask

---

