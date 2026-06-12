---
title: "suspend"
date: 2008-10-23
forum: Hardware
---

### Post by uvdevnull on 2008-10-23
Since I installed Ubuntu on my Sony Vaio a couple of months ago, it was able to suspend just fine, but after the last round of updates which I believe included a kernel update, I've been unable to come out of suspend. It goes to sleep just fine, but then doesn't come out and I have to kill it.  Not sure where to start looking for a solution...

Thanks,
uvdevnull

---

### Post by Cl0ud9 on 2008-10-23
Try installing/reinstalling the latest Nvidia or ati drivers. I do this after every kernel update to get everything working properly.

---

### Post by uvdevnull on 2008-10-24
> **Cl0ud9 said:**
> Try installing/reinstalling the latest Nvidia or ati drivers. I do this after every kernel update to get everything working properly.

This lappy has an Intel graphics.  Keeping in mind my noob status, how would I reinstall those drivers?  I didn't have to install anything special after the initial OS load, it just worked right out of the box, just like they promised :)

Thanks man!

---

### Post by uvdevnull on 2008-10-25
I tried...
```
sudo apt-get --reinstall install xserver-xorg-video-intel
```
but it didn't help. :(

---

### Post by Cl0ud9 on 2008-10-25
Try using envyng.

```

sudo apt-get install envyng-core

envyng-t

```

Then follow the directions.

---

### Post by phidia on 2008-10-25
Envy/envyng is only for the installation of nvidia and ati proprietary drivers.
See the [envy site]("http://albertomilone.com/nvidia_scripts1.html") if you need to verify that.

With an intel gpu you do not need to enable anything it does work out of the box. 
So don't install envy it won't do anything for you.

I'm not sure why suspend isn't working though and suspend/resume issues can be complicated.

You could try booting using the previous kernel, and if it works with that you could file a bug report.

---

