---
title: "Can I upgrade to 8.10 if I have a Quadro2 MXR - NV11GL?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by montysan on 2009-02-24
I've tried searching these forums, and the web in general, but I'm struggling to find a definitive answer for this exact graphics card. I'm currently using Ubuntu 8.04.

glxgears -info gives this info about my card. Is this the best way to find out what card you have - I inherited this machine and know nothing about it.
GL_RENDERER   = Quadro2 MXR/AGP/SSE2
GL_VERSION    = 1.5.8 NVIDIA 96.43.05

Also, is there a way to test the new graphics drivers before upgrading?

Any help much appreciated.

---

### Post by montysan on 2009-02-24
If I download a LiveCD of 8.10, will I be able to use this to test if my graphics card will work with the accelerated drivers?

My internet connection is not particularly fast, so I don't want to do this unless it's a reliable way of testing the driver situation.

---

### Post by cb951303 on 2009-02-24
we still have nvidia 96 drivers in 8.10. I don't see why it wouldn't work.
[http://packages.ubuntu.com/search?keywords=nvidia-glx-96&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=nvidia-glx-96&searchon=names&suite=intrepid&section=all)

---

### Post by montysan on 2009-02-24
Thanks for the reply, but it's this bit in the release notes that's stopped me automatically updating. 

> The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

I've used Ubuntu for quite a while, but I've never had to look into graphics issues before, and I'm finding it very hard to work out how to get to the bottom of this. I don't fancy losing acceleration, as I remember what it was like before I got it going the first time.

---

### Post by cb951303 on 2009-02-24
Oh, that makes me doubt my previous post but intrepid nvidia-glx-96 package description clearly states that your card is supported with hardware acceleration so I doubt it defaults to nv module.
Or they just forgot to change package description which is unlikely :lolflag:

EDIT: OOPS, WAIT. No quadro2 sorry! I guess you're stuck with 8.04 if you want hardware acceleration. You see the disadvantage of proprietary drivers :) ??

---

### Post by ikisham on 2009-02-24
It will work fine with a few buts..(details in the next post)

---

### Post by ikisham on 2009-02-24
I have a GF4MX460 that uses the same 96 series driver. I've downgraded from 8.10 to 8.04 a few days ago but the motive was not the video card, actually it works BETTER in Intrepid (version 96.43.**10** against 96.43.**05** in Hardy).(more details coming...)

---

### Post by theozzlives on 2009-02-24
Sorry to barg in, but why does everyone recommend nvidia when I read about so many probs with them?

---

### Post by ikisham on 2009-02-24
But you must tweak a little something in /etc/X11/xorg.conf for OpenOffice to work fine. See here:
[http://ubuntuforums.org/showthread.php?t=990134&page=2](http://ubuntuforums.org/showthread.php?t=990134&page=2)
'bug' description here [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076)
Also in Wine you must tweak:
[http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71](http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71)
All very easy. So again: your card will work better in 8.10 (I see some artifacts in Hardy that I didn't see in Intrepid). If you're only experimenting then it's ok to change to Intrepid, but if not you may weigh if you want to shorten the support you'll receive cos both systems are much alike (only Intrepid and the softwares are a bit more modern).

---

### Post by ikisham on 2009-02-24
> **theozzlives said:**
> Sorry to barg in, but why does everyone recommend nvidia when I read about so many probs with them?

Hey mate, do you know what a 'Quadro2 MXR - NV11GL' is? If I'm not wrong that must be like an almost turn-of-the-century card. And it was/is a great card for those oldies (it's much better than those 8MB on-board vids);)

---

### Post by cb951303 on 2009-02-24
> **theozzlives said:**
> Sorry to barg in, but why does everyone recommend nvidia when I read about so many probs with them?

because ATI is even worse :D

---

### Post by montysan on 2009-02-24
Cheers for the replies everybody. Still not sure whether to try the upgrade though :p.

I have to say I didn't choose the card (free ancient pc from work, and I just can't bring myself to spend any money at all on it), but it's been doing great for what I use the pc for until now. Why get a new one if it ain't broke.

Loving Ubuntu, and are slowly bringing others round at work to it's vertues. However, some of these issues make it very hard to recommend it to others, as they're so hard to chase up yourself. Mind you....windows isn't always easy, what with all the blue screens from graphics drivers.

---

### Post by ikisham on 2009-02-25
I'll reproduce my PM to you as it may be useful for other people:

"I remembered that I heard something about Google Earth not working because of that 96 driver issue and I don't know if there was a workaround. All in all, maybe all this will be fixed for Jaunty (to be launched April 23rd) and also there will be other improvements like I hear it'll boot up faster. If your hardware is somewhat less powerful, another tip would be that you keep Hardy so you get used with Linux (if you're not already) and then someday upgrade to another Linux distribution that could work really fast in that pc. There are many modern, full-featured distros nowadays and many are meant to be used with less powerful machines. Most of them are so easy to use as ubuntu and the usability will get better and better as Linux evolves."

---

### Post by montysan on 2009-02-25
Thanks again, and I think I might wait until the next big release and see what the release notes say then.

I just wish, as this graphics stuff can have a massive impact on your install of Ubuntu, that there was a clearer way of working out if your card is supported etc. All this 

> The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu

is just not that clear to me.

---

