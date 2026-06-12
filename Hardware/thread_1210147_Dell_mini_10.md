---
title: "Dell mini 10"
date: 2009-07-11
forum: Hardware
---

### Post by mrwoody on 2009-07-11
Hi *. 
Does anyone knows what are the news regarding ubuntu on dell mini 10?
does it work well? 
does it support the 1,366 x 768 resolution? 
does it support multi-touch? 
does/will it support the new GPS feature?

**Thanks**

---

### Post by mrwoody on 2009-07-14
anyone?

---

### Post by mikewhatever on 2009-07-14
If you buy one with Ubuntu pre-installed, I suppose it will support the native resolution. Dell ships its notebooks with the 8.04 version, not a problem, just something to be aware off. Jaunty works well, but requires a relatively simple fix to get the correct resolution.
I bought a mini 10 and installed 9.04. It has no multi-touch features other then taping and two finger scrolling, but Dell's custom version might, I don't know.
Check out this blog for more info:
[http://mok0.wordpress.com/2009/05/22/ubuntu-on-the-dell-mini-10/](http://mok0.wordpress.com/2009/05/22/ubuntu-on-the-dell-mini-10/)

---

### Post by tyroeternal on 2009-07-14
I would HIGHLY recommend the Mini 10v over the Mini 10 (and the Mini 12).  The 10v uses the Intel GMA 950, and the 10 (and 12) use the Intel GMA 500.

As of right now, there is no joy to be had for GMA 500 users like myself.  The video drivers are bad.  In their current stat they provide nothing more than the correct resolution.  Bad 2d support and no working 3d support at all.

The 950 performs well enough in jaunty, and will be doing great under karmic when they move to the new kernel (along with a few other improvements).

---

### Post by cloudjy on 2009-07-14
The graphic driver for GMA500 is available from the following URL:

[https://launchpad.net/~ubuntu-mobile/+archive/ppa](https://launchpad.net/~ubuntu-mobile/+archive/ppa)

---

### Post by tyroeternal on 2009-07-14
I am using that already, and that was what I was talking about.  The 2d support is horrible... essentially only giving the correct resolution.  There is no hardware accel., and the 3d is both bad and causes system lockups.

---

### Post by mikewhatever on 2009-07-14
> **tyroeternal said:**
> I am using that already, and that was what I was talking about.  The 2d support is horrible... essentially only giving the correct resolution.  There is no hardware accel., and the 3d is both bad and causes system lockups.

Have you installed UNR or Ubuntu/Gnome? I've been experimenting with the mini 10 and settled on LXDE with Skype, a browser and a media player. The system is a bare minimum by Ubuntu standards and isn't as easy to use, but it's been much snappier, and handled Skype calls and flash rather well. Just a thought, Xubuntu might be a better option for a full desktop installation.

---

### Post by mrwoody on 2009-07-14
> **cloudjy said:**
> The graphic driver for GMA500 is available from the following URL:

[https://launchpad.net/~ubuntu-mobile/+archive/ppa](https://launchpad.net/~ubuntu-mobile/+archive/ppa)

Thanks! which file is needed? and doc?

I actually ordered a mini 10 (which does not ship with ubuntu unfortunately and has a gma500 ) because it is the one with the best resolution (around 720p). I hope I can run linux on it soon! ;-)

---

### Post by mrwoody on 2009-07-14
> **tyroeternal said:**
> I am using that already, and that was what I was talking about.  The 2d support is horrible... essentially only giving the correct resolution.  There is no hardware accel., and the 3d is both bad and causes system lockups.

Which screen do you have?
Also, are you able to use multi-touch?

---

### Post by mikewhatever on 2009-07-14
> **mrwoody said:**
> Thanks! which file is needed? and doc?

I actually ordered a mini 10 (which does not ship with ubuntu unfortunately and has a gma500 ) because it is the one with the best resolution (around 720p). I hope I can run linux on it soon! ;-)

You need **xserver-xorg-video-psb** package. There are more detailed instructions here [http://ubuntuforums.org/showpost.php?p=7589740&postcount=727](http://ubuntuforums.org/showpost.php?p=7589740&postcount=727).

---

### Post by Hillbilly1950 on 2009-07-14
Hi all

First post on the forum, but been following it for quite some time. Full of useful info.

Have recently purchased a Dell Mini 10, and followed the above instructions, now i have the full resolution, running Xubuntu. Only in 2D mode for now, but looks clear and circles are round !!

Thanks

---

### Post by mrwoody on 2009-07-15
> **Hillbilly1950 said:**
> Hi all
Have recently purchased a Dell Mini 10, and followed the above instructions, now i have the full resolution, running Xubuntu. Only in 2D mode for now, but looks clear and circles are round !!


Thanks for the info. This makes me feel better (since I already ordered one).
Just out of curiosity, what would the 3d support in a netbook be useful for?

---

