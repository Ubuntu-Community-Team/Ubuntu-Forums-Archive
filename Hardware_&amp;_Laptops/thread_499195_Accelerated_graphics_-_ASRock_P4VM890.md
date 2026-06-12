---
title: "Accelerated graphics? - ASRock P4VM890"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by xelapond on 2007-07-12
I just built a new Linux box, upgrading from an old pentium three.  I had a Celeron 2.5 ghz laying around, so I used that.  The motherboard I bought has integrated graphics, and i figured that would ne fine because I wouldn't be doing any gaming.  Is there a way to get the accelerated graphics for the integrated, just so certain things are a bit snappier.  And is it remotely possible to get beryl running, or is that out of the question?

Alex

---

### Post by bdtgp on 2007-07-12
Go to System>Preferences>Desktop Effects and enable the driver.  After this you will need to restart.  Then you can go ahead and install Beryl or Compiz Fusion.  I'm not sure how snappy it will be since I'm not running on integrated graphics but its worth a shot, you can always uninstall it.

---

### Post by jocko on 2007-07-13
> **bdtgp said:**
> Go to System>Preferences>Desktop Effects and enable the driver.  After this you will need to restart.  Then you can go ahead and install Beryl or Compiz Fusion.  I'm not sure how snappy it will be since I'm not running on integrated graphics but its worth a shot, you can always uninstall it.

That would perhaps work if he had an ATI or nvidia graphics card that actually have restricted drivers... Unfortunately he has a built-in VIA unichrome chipset...

> **xelapond said:**
> I just built a new Linux box, upgrading from an old pentium three.  I had a Celeron 2.5 ghz laying around, so I used that.  The motherboard I bought has integrated graphics, and i figured that would ne fine because I wouldn't be doing any gaming.  Is there a way to get the accelerated graphics for the integrated, just so certain things are a bit snappier.  And is it remotely possible to get beryl running, or is that out of the question?

Alex


Either try this:
```
sudo dpkg-reconfigure xserver-xorg
```
And set it to use the "via" driver.

If that doesn't work try:
```
sudo apt-get install xserver-xorg-driver-unichrome
```
And then:
```
sudo dpkg-reconfigure xserver-xorg
```
(find the correct driver in the list, I guess it will be called "unichrome")

**Note:** I don't know if any of the above will work. Also from what I can see from googling around a bit, they provide 2d acceleration and maybe tv-out but not 3d acceleration. I may be wrong. If it doesn't work, just run the dpkg-reconfigure command again and select "vesa".

---

