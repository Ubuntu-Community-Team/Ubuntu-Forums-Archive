---
title: "[SOLVED] FGLRX with 780g (HD3200) doing funny stuff."
date: 2008-09-20
forum: Hardware
---

### Post by travm on 2008-09-20
Hi, I have been messing with ubuntu 8.04 on my desktop now since release, and have been having trouble with my video drivers.  No open source driver will work for me (except vesa, and i get stuck at 640x480, which is too small).  Currently I have the binary (ati.com) driver worker (version 8.7),  but only partially.  I think the problem is related to the fact I have it connected to my HDTV via HDMI.  When I disable (turn off) my tv I can boot into Ubuntu and everything works fine.  When I leave my tv on and try to boot the login screen appears too big for my screen (virtual size 1600x1200 ish).  If I make any changes in ati catalyst control centre, it destroys my xorg.conf file.

Now to how to fix this.  I would like to know if there is a way I can force my HDMI output to be display 2, currently it defaults to display 1 as shown in ATI CCC.  
My goal is to use this as an HTPC / Home pc to run on both my monitor and on my tv.  just like i can easily do in windows.
Any guidance would be appreciated.
oh, and by the way, fglrxinfo reports mesa as my driver.  what gives?

---

### Post by markbuntu on 2008-09-20
First, you need to fix the mesa problem. Look in Xorg.0.log for something about DRI not being enabled. If it says there may be missing kernel modules then the driver was not properly installed. Also, if you have xserver-xgl installed, you really need to remove it because it will prevent the driver from working properly and also cause the reversion to mesa. If you got the driver with envy or ran the installer, the driver may have been misinstalled.

The only method for installing the driver that I have found to work properly is Method 2 here:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

As of right now, it will get you the 8.8 driver but I suspect it will be updated for 8.9 very soon. Each new driver from ati has more options for setting up tvs and 8.8 has more than 8.7 which will probably help your situation. You can find these options with aticonfg --help as they are not yet integrated into the CCC.

---

### Post by travm on 2008-09-21
It says Missing kernel module or something.
How exactly could I not install the driver correctly?
I followed the steps in that guide, except I did use the wrong driver version, so i'll assume thats part of the problem.  It gets really hard to set things up at 640x480.  I'm on dialup so I am downloading the 8.9 Cats now.  I am going to try to install them following that guide tommorow.  Maybe it will work better with my television.  Thanks for the tips.

---

### Post by travm on 2008-09-22
Trying to build the drivers i got a failure and it says it couldnt find LibGL.something.
Any help?

---

### Post by travm on 2008-09-22
this is what the driver build outputs,
I am omitting most of the stuff that worked
```
dh_makeshlibs -pfglrx-modaliases  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx    
dpkg-shlibdeps: failure: couldn't find library libGL.so.1 needed by debian/xorg-driver-fglrx/usr/sbin/atieventsd (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.r12555

```
Also I checked, and libGL.so.1 is present in my /usr/lib directory.

---

### Post by travm on 2008-09-22
Solved it,
It wasnt actually libGL.so.1 it was libGL.so , so I created a symlink to libGL.so as libGL.so.1 with teh following
```
sudo ln -s /usr/lib/libGL.so /usr/lib/libGL.so.1
```
Cats 8.9 work fine,
mesa problem in non existent, basically, this driver fixed everything.

---

