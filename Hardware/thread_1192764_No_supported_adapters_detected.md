---
title: "No supported adapters detected"
date: 2009-06-20
forum: Hardware
---

### Post by prions on 2009-06-20
Trying to update my ati drivers. 

I've been following this: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

guide, and its gone well up until step 5.

But, once I type in "sudo aticonfig --initial -f" I get "No supported adapters detected"

I'm running an ATI Radeon Xpress 200m

My worry is its not supported, if its that, should I install Ubuntu 8?

---

### Post by derekweber on 2009-08-11
I get the same error at step 6 (I have a 32-bit system, not 64-bit) from the same guide, but I'm using Ubuntu 9.04 with a ATi Radeon 9600XT AGP video card in an AMD system.

I'm tempted to reboot the system to see what happens, and frankly I'm not sure what the alternative is (although I could undo the changes to /etc/X11/xorg.conf and then reboot, which should return the system to its original state).

Any tips anyone?

---

### Post by derekweber on 2009-08-12
I can certainly confirm that I'm a dunce. I think the guide could be worded a little more clearly, but if your video card (like mine) is on the list of cards no longer supported that it links to, *then there is NO point* in attempting to install the ATi drivers - in fact, if you get as far as step five, make sure you uninstall the debs before rebooting otherwise your screen goes away. :o)

I tried the OSS drivers and the 'radeon' one works for me (xserver-xorg-video-radeon) but the 'radeonhd' one doesn't (xserver-xorg-video-radeonhd), and I can't tell a difference between the 'radeon' and the default 'ati' one that comes with Ubuntu Jaunty in the first place.

Sorry for the red herring.

I hope you find a solution - perhaps bug the author of the guide?

---

### Post by derekweber on 2009-08-12
> **prions said:**
> 
I'm running an ATI Radeon Xpress 200m


Yeah, the link here [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4) that the guide links to indicates your Xpress 200m is one of the unsupported lines of ATi cards.

Bummer.

---

### Post by barretr on 2009-10-05
Try [downgrading]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue") your xserver.

---

### Post by Xethron on 2010-05-14
> **derekweber said:**
> I can certainly confirm that I'm a dunce. I think the guide could be worded a little more clearly, but if your video card (like mine) is on the list of cards no longer supported that it links to, *then there is NO point* in attempting to install the ATi drivers - in fact, if you get as far as step five, make sure you uninstall the debs before rebooting otherwise your screen goes away. :o)

I tried the OSS drivers and the 'radeon' one works for me (xserver-xorg-video-radeon) but the 'radeonhd' one doesn't (xserver-xorg-video-radeonhd), and I can't tell a difference between the 'radeon' and the default 'ati' one that comes with Ubuntu Jaunty in the first place.

Sorry for the red herring.

I hope you find a solution - perhaps bug the author of the guide?

Hey,

I just got this error and Luckly I didn't restart yet... How do I "uninstall the debs"? Is the following command correct or did I misunderstand you.
```
sudo apt-get remove fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases
```

Thanks
Xethron

---

