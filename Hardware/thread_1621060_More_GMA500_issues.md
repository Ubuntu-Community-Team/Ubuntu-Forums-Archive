---
title: "More GMA500 issues"
date: 2010-11-13
forum: Hardware
---

### Post by dean_the_great on 2010-11-13
I'm not sure if this should go here, but the huge thread [Guide to Get the Best Performace from the GMA 500]("http://ubuntuforums.org/showthread.php?t=1229345") is too daunting for me.

I'm running an Asus Aspire One 532h-2727 and the GMA500 graphics driver has been giving me huge issues. Although I had it working fairly well, I decided to try some new drivers and now I've throughly messed myself up.

I installed all the poulsbo drivers using this command:


```
sudo add-apt-repository ppa:gma500/ppa && sudo aptitude update && sudo aptitude install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config
```

And I followed the instructions on the first page, but now I can only boot into low graphics mode. I've done some finaggling, browsing all the threads I could find on the subject, but now I'm stumped.

When I type:

```
sudo modprobe psb
```

I get:

```
FATAL: Error inserting psb (/lib/modules/2.6.32-25-generic/updates/dkms/psb.ko): Cannot allocate memory
```

Any ideas? I'm a total newbie when it comes to linux....

---

### Post by cr0m on 2010-11-13
Are you running Lucid (10.04) or Maverick (10.10)?

---

### Post by dean_the_great on 2010-11-13
I'm using Lucid 10.04, kernel 2.6.32-25-generic

I've tried uninstalling all the poulsbo drivers and re-installing fbdev (and changing xorg.conf to match), and now it doesn't boot into low graphics mode but it still won't let me change any desktop effects and it's still acting like it's in low graphics.

---

### Post by dean_the_great on 2010-11-15
Wow, at this point I'd wish I'd just been satisfied with the graphics I had, instead of trying to enable 3D acceleration.

I'm still running with very low graphics. Even after reinstalling fbdev and all the compiz packages that poulsbo had uninstalled.

Could I be missing more packages associated with fbdev, or am I better off reinstalling poulsbo 2d and 3d and trying to get that to work?

---

### Post by lucazade on 2010-11-15
Your netbook doesn't have gma500 but Intel Atom N450 / 1.66 GHz
please paste "lspci" output here!

---

