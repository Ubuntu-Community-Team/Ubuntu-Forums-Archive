---
title: "Gutsy nvida driver much faster than Hardy"
date: 2008-08-02
forum: General Help
---

### Post by superyounan1 on 2008-08-02
A few days ago I finally got tired of my ATI card and bought an old nvidia 7600. I installed it into my Gutsy computer and installed the driver recommended by the restricted driver manager, which turned out to be the nvidia 100.xx.xx driver. 3D was perfect! although 2d was sluggish.

I then did a clean install of Hardy and installed the driver recommended again, this time it was the nvidia 169.xx.xx. Performace was poor compared to the old driver! it was really disappointing. 

So I installed Envy and now I have driver version 173.14.19, the latest available for my card, and it is quickyer than the 169.xx.xx, but still not as good as the old 100.xx.xx! 

I can really feel the difference with wobbly windows, and glxgears gives about 1/5 the frame rate :(

what gives? do i need to tweak my xorg.conf?

Also, 2D was better on my ATI! :(

---

### Post by steveneddy on 2008-08-03
I've had to tweak my xorg.conf to get the best out of my Nvidia card, just like on Gutsy.

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	[B]Option          "AddARGBVisuals"        "True"
       Option          "AddARGBGLXVisuals"     "True"
	Option          "TripleBuffer"         "True"[/B]
	Option		"NoLogo"	"True"
EndSection

```

These lines added to my xorg.conf file made the difference in my rendering very well.

Any video in just stunning.

The monitor on my laptop only goes to 1280x800.

---

### Post by superyounan1 on 2008-08-03
oh wow, thanks for the reply. I made the changes you suggested, but unfortunately I don't see much of a difference.

The new 177 beta driver has been recommended to me, others have reported significant performance boosts. Mayhaps i'll look into that

---

### Post by steveneddy on 2008-08-04
> **superyounan1 said:**
> oh wow, thanks for the reply. I made the changes you suggested, but unfortunately I don't see much of a difference.

The new 177 beta driver has been recommended to me, others have reported significant performance boosts. Mayhaps i'll look into that

That may help.

Frankly, I just use whatever is in the repos.

Works for me and seems a little more stable.

---

