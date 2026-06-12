---
title: "[SOLVED] Installing tint2"
date: 2008-10-10
forum: General Help
---

### Post by OutOfReach on 2008-10-10
Hey, I am currently using PyPanel along with Openbox3 but I found tint2 and I want to try it.

I downloaded the 0.6 source from their google code page. I go into the src directory and I perform:
```
make
```
and it outputs: ```
cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
strip tint

``` which I think is good.

Then I do *sudo checkinstall* instead of *sudo make install*

but it fails and outputs:
```
(Reading database ... 163205 files and directories currently installed.)
Unpacking src (from src_20081010-1_i386.deb) ...
dpkg: src: warning - conffile `etc/xdg' is not a plain file or symlink (= `/etc/xdg')
dpkg: error processing src_20081010-1_i386.deb (--install):
 unable to create `./etc/xdg/tint/tintrc': No such file or directory
Errors were encountered while processing:
 src_20081010-1_i386.deb

```

---

### Post by OutOfReach on 2008-10-10
Nevermind I got this.

---

### Post by vincenma on 2008-12-14
Hi,

here is a temporary 'solution' : 
simply recreate the missing dir files...



```

cd /etc/xdg/
sudo mkdir tint2
```

---

### Post by Piraja on 2009-02-01
FYI, tint2 can be most easily installed on Intrepid via [toodumbforgentoo's]("http://urukrama.wordpress.com/2008/07/23/tint2/#comment-299") [PPA]("https://launchpad.net/~k-belding/+archive/ppa") repo:

deb [http://ppa.launchpad.net/k-belding/ppa/ubuntu](http://ppa.launchpad.net/k-belding/ppa/ubuntu) intrepid main

Just add the line above to your /etc/apt/sources.list, perform "sudo apt-get update" and "sudo apt-get install tint2".

---

