---
title: "Screen Resolution"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by dgoodma on 2008-02-18
HP/Compaq nc8430 laptop with Radeon Mobility X1600 graphics.

Having issues setting and keeping a screen resolution. Tried the proprietary drivers, that only allowed 640 X 480. Took those out, Now shows vesa Generic vesa compliant. This allows me to change things, but the next time I login in; it complains about needing to run in Low Res mode, graphics card cannot be determined, configure, or continue... either choice then lets me in, and works. If I select Test, the screen flashes, goes to login screen, but the resolution holds and works. But, log out, and this has to be done all over.

At one point I had everything working great, including the deskop effects; and then I plugged in an external monitor, and "it lost its mind", and now I am losing mine.

How do I get this to a state where I can set and hold the resolution. Very confusing, and frustrating, I would say this area is the single most frustrating part of using Ubuntu; like all else....

Is there a single source of how to do this?

Why doesn't the OS understand how to read and apply the correct graphics?

---

### Post by Yellow Pasque on 2008-02-19
Try the proprietary drivers again. They're the best option if you want desktop effects:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f
```

If you don't care about desktop effects or 3D and just want a good 2D driver, the open-source radeonHD driver is the best bet.

---

### Post by SantinoC on 2008-03-07
> **Temüjin said:**
> Try the proprietary drivers again. They're the best option if you want desktop effects:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f
```

If you don't care about desktop effects or 3D and just want a good 2D driver, the open-source radeonHD driver is the best bet.

ive got the same problem and I've tried reinstalling the fglrx drivers, ran the config. and i even manually put in the proper res for my monitor(1680x1050) and still it defaults at 1600x1200.

im stumped

---

### Post by kalinblajev on 2008-03-07
Dudes, i am joining you - same problem. If you find a way to fix it, please post it. Thanks

---

### Post by SantinoC on 2008-03-08
i have figured out the problem.

in the CompizConfig "General" section the Display was set to 1600x1200, so im assuming everytime compiz was being initialized for the first time it was resetting the screen resolution, since setting it to the proper resolution(in my case 1680x1050) it loads perfect now, and i officially have my linux box setup exactly how i want it.

Now if i can only get MonoDevelop to stop crashing on me then id be truly set.

---

### Post by seijling on 2008-03-09
There is also the simple task of changing the xorg.conf file to somethign like:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Mobility Radeon X1600"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
EndSection
```

I have only listed my native resolution however, any combination can be used.

You can edit your xorg.conf file with the following (sequential) commands:

```
cd ..
cd ..
cd etc
cd X11
sudo gedit xorg.conf

```

and change the subsection "Display" to include the modes of interest.

Hope this helps.

Mike

---

### Post by SantinoC on 2008-03-10
i did that already to my xorg.conf file and it was still booting up in 1600x1200 mode, even though the only resolution listed int he xorg file was 1680x1050. it was weird though, one a cold boot up it would boot up int he wrong resolution, but then if i did a soft restart it would boot up in the proper resolution.

and since changing the resolution in compiz its working perfect now, so im assuming a combination of that and the change in the xorg is what does it.

---

