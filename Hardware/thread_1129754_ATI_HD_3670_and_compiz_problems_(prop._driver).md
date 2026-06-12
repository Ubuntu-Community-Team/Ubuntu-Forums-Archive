---
title: "ATI HD 3670 and compiz problems (prop. driver)"
date: 2009-04-19
forum: Hardware
---

### Post by PauGNU on 2009-04-19
Hi

I'm having some problems on my Dell Studio XPS with ATI HD 3670 graphics card. The thing is the only way to enable compiz is using the proprietary driver.

Once installed, everything works fine. But when I enable Compiz it works, but everything stops working smooth. I mean, when I want to maximize a Windows and click on the maximize button, it takes maybe one second to do it. It seems like it freezes for a few milliseconds...

I tried with the driver from the repositories and the one from the official amd website. 

Also, this happened to me before in other ATI cards when using the proprietary driver.

Is there a parameter or a thing that I can modify in order to avoid these problems?.

Thanks!!

---

### Post by mosimea on 2009-04-19
Are you running Jaunty?  I understand that the latest flgrx is available in the Jaunty repositories. I believe that it is version 9.4, also released on ATI's now here: [URL="http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English"]http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English
[/URL]
I've purchased the same laptop (expecting delivery on the 29th) and am hoping that Compiz and 3d are working smoothly with the new drivers.  Searching the boards here, it seems that some people are having success with 600 series cards and the new proprietary drivers.

Other than the video card, how have things worked with the Studio XPS and Ubuntu?  Wireless, bluetooth, sound, webcam, and trackpad working out of the box?

---

### Post by PauGNU on 2009-04-20
Yes, I'm running Jaunty. I tried the lastest one and still the same, it doesn't work smoothly... and that's really annoying.

At this moment I'm working with the radeon driver, at least it allows me to use the metacity compositing and I can use the awn. 

Maybe in a few months...

---

### Post by bmdavis on 2010-03-02
any update on this?   I have the same problem in Karmic with the new ATI drivers.  Elements of COmpiz work great (cube and special effects), the minimizing and resizing windows is quite slow...

3670 with studio 1640

---

### Post by keith_emerson on 2010-04-04
Hi...This problem has been resolved

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

you can check for the "no backfill" patch ;)

---

### Post by PauGNU on 2010-04-24
The backfill still present in Lucid when using fglrx driver. But we can apply the patch:
[http://www.somgnu.cat/2009/10/03/evitar-el-backfill-amb-el-controlador-fglrx-a-ubuntu-karmic/](http://www.somgnu.cat/2009/10/03/evitar-el-backfill-amb-el-controlador-fglrx-a-ubuntu-karmic/)

It's really easy to do so:
```
wget http://launchpadlibrarian.net/32728179/xserver-xorg-backclear.patch
sudo apt-get install devscripts
sudo apt-get build-dep xorg-server
apt-get source xorg-server
cd xorg-server-1.6.3
patch -p1 < ../xserver-xorg-backclear.patch
debuild
cd ..
sudo dpkg --install xserver-xorg-core*.deb
```

There was a ppa repository providing patched xorg packages, but there is no version for lucud, so we can use this way.

---

