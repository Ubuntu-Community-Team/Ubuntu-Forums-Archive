---
title: "Man, I give up.  ATI vs. Karmic"
date: 2010-01-29
forum: Hardware
---

### Post by Shibblet on 2010-01-29
I have tried.  I've searched for a usable fix.  I've looked and looked and looked.  About halfway through this search, I actually found the Holy Grail, it was a tad easier.

I have an MSI Wind L2100, it has an ATI x1250 Mobile Graphics Adapter built in.  It also has an RaLink 3090 Wireless Adapter.

Karmic will install.  I cannot get the video drivers to work, and I can only get the wireless adapter to work if I don't upgrade the kernel.

I've tried working with the new open source ATI drivers, and they don't function well at all.

I've learned the problems, the xserver isn't compatible with current ATI drivers.  So I've tried downgrading the xserver.  That didn't work either.

I hate to say it, but for functionality, this Notebook is Karmic-Proof.  My only option at this point is to either sell the Notebook and get one that works, or run Windows 7.  Which does work, but is still using Vista Legacy Drivers.

---

### Post by Shibblet on 2010-02-01
The only option I really have at this point is to add

```
ppa:xorg-edgers/ppa
```

to my repository.  This gives me great 2D, but really bad 3D.  Which is fine, at least my video playback is great.  

After adding the PPA, all I did was run an update, and the new updates for the current drivers were replaced.  

I highly recommend this for anyone using legacy ATI Video.

So, I might have to change the title of the thread to...

***Man, I give up.  ATI vs. Karmic - But came to terms.***

---

### Post by Shibblet on 2010-02-01
And just to add a bit more to this fun.  This computer, the MSI Wind L2100 comes with Windows 7.  And on the driver CD, the ATI Catalyst drivers for Windows 7, are actually Vista Legacy Drivers, and unfortunately the only ones available.

I update the ATI Xorg-Edger drivers on Kubuntu, and now my Notebook will play video back perfectly.  Even 720p, and 1080p video content.  As a matter of fact, Kubuntu and Mplayer will play Big Buck Bunny (I used it to test) in 1080p.

Windows 7 and the ATI Legacy Drivers will not play it in 1080p without a lot of choppyness and dropped frames.

Tell me if I am seeing this the wrong way, but seems to me like the Xorg-edger drivers are better than the ATI Catalyst Vista Legacy Drivers.

---

