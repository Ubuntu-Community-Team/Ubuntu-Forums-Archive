---
title: "I can't watch TV with an ATI 9550 video card and Leadtek TV2000XP"
date: 2008-08-13
forum: General Help
---

### Post by Sycron on 2008-08-13
I have the following hardware: **Leadtek TV2000 XP Expert** and **ATI 9550 video card**.

When i'm trying to run tvtime I get the following messanges on terminal
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/alla/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```
I've also tried with **xawtv**(that blanked my screen) , and **me tv** which doesn't detect my tv tunner card.

I tried [this](http://ubuntuforums.org/showthread.php?t=215763) tutorial but it is outdated and doesn't work on hardy.

Any sugestions are welcome.Thanks.

---

### Post by Sycron on 2008-08-13
So , after one day gone i made it :). This is what i've done. I've booted the LiveCD Ubuntu 7.10 , installed tvtime and it worked.... I looked on the xorg.conf and i discovered if I add to section under device the following line TV would work.
```
driver "ati"
```

It will never work with other settings.... So if someone will be in my situation I hope that i can help him :)

---

