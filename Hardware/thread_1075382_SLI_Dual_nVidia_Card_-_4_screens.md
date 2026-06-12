---
title: "SLI? Dual nVidia Card - 4 screens?"
date: 2009-02-20
forum: Hardware
---

### Post by dchurch24 on 2009-02-20
Hi all,

I've been using Ubuntu for some time (since 6.04) and Xubuntu & Edubuntu on my kids machines, plus XUbuntu on my xbox, and Ubuntu on my main PC.

I've started to use Ubuntu Studio on a slightly older machine for music recording, and everything is going great - the only problem I have now is the lack of hours in a day to get in the room to do more recording (it's the most addictive thing I've ever done!)

Despite having 2 22in wide screens, I still find myself getting short of room once I have Arduour (with mixer), Hydrogen, JAMin etc... up and running.

I also have another 2 22in wide screens on another machine - total 4.

Shortly we are moving house and the misses says I mustn't have a PC in the living room any longer, and so I thought that as the one in the living room is the most powerful, I would use it for music recording.

Now this means that the recording machine is going to become redundent (and quite probably a Myth front-end box).

If I take the graphics card from the recording box - a PCI-E nVidea FX (something, can't remember model, but it DOES have SLI), and put that in my other box which has a PCI-E nVidea 7600GS in it, is it just a case of linking the two together with the cable and plugging two screens into each, or do the cards have to be the same make/model?

...has anyone else done this, and if so, what troubles am I likely to experience?

---

### Post by wstout on 2009-02-20
I am by no means an SLI expert, but I do have it running on my Ubuntu 8.10 machine. According to everything I have seen the cards have to be identical. I have read most places that they have to be the same, maker, model, etc. But, I have also seen results from some people who say that as long as it is the same chipset it will work, for instance two gt9800 or whatever you have. It looks like you have everything different so I don't think you can get SLI working, but I think you can set both of those cards up for four monitors. In my initial setup that's what I had, but both of my cards where the same so that could have led to me being able to do it that way.

Why not slap it in and see what happens? :) Oh yeah from my experience, you better plan on doing some hacking of the xorg config files, and expect to totally break X a time or two before you get it working :\

---

### Post by Squid Spectre on 2009-02-20
I don't think that will work with those particular cards, not until HYDRA starts being shipped on MBs at least.

I'll be the first to admit I don't keep up with the bleeding edge news on SLI but I believe that SLI simply can't handle multiple screens. It's meant for more of a graphics acceleration thing, which I suspect you don't really need if you use it for recording and media playback. It could be just a syntatical misinterpretation. The good news is you should be able to accomidate all four of your monitors on two different nVidia cards without SLI, in fact its the only way to do it that I'm aware of. The only problem you will likely see is that each card will want to have its own X session which can cause some unwanted behavior depending on how you use it.

---

### Post by wstout on 2009-02-20
Squid Spectre: actually on they latest update to the Nvidia drivers (Vista) you can SLI with multiple monitors (I haven't tried this but it is an available option on my cards). On the Vista side of things you can set your monitors up and have one monitor to be the sli focus monitor with the others not receiving the extra "strength" so to speak. I'm not for sure though about Ubuntu I just use one monitor currently.

---

### Post by Squid Spectre on 2009-02-20
About time they did that, thanks for the update.

---

### Post by wstout on 2009-02-20
Exactly I couldn't beleive that when I first installed my sli setup. But, like I said I haven't tried it in Vista, and I'm guessing it will work in Ubuntu also but haven't even looked there since I lost my second monitor to the wife.

---

### Post by dchurch24 on 2009-04-17
Hi all, well I got it all up and running with 4 monitors - and all is good!

...apart from I seem to have one x session on the first two monitors and a different x session on the next two (so you were spot on Squid Spectre!).

The programmes talk to each other fine (I can open Jamin on the first session and Ardour on the second and it's all fine).

I was wondering if it's possible to have all four monitors using the same x session?  I can't find a setting anywhere that lets me do this.

---

### Post by BKing600 on 2009-06-02
> **dchurch24 said:**
> Hi all, well I got it all up and running with 4 monitors - and all is good!

...apart from I seem to have one x session on the first two monitors and a different x session on the next two (so you were spot on Squid Spectre!).

The programmes talk to each other fine (I can open Jamin on the first session and Ardour on the second and it's all fine).

I was wondering if it's possible to have all four monitors using the same x session?  I can't find a setting anywhere that lets me do this.

I'm planning to do the same thing (2 nvidia cards, 4 monitors). **Any news about the 2 different x sessions?**
I'd REALLY like to resize blender to use all 4 screens.

dchurch24:
a) When you use nvidia-settings, does it show 4 monitors (that you can move around) in the "X Server Display Configuration"?

b) Did you try to enable Xinerama too? Does that help (to combine the 2 x sessions)?

Thanks!

---

