---
title: "[SOLVED] Grayscal font smoothing"
date: 2008-10-31
forum: General Help
---

### Post by klange on 2008-10-31
Alright, don't normally find myself in a support forum, but this has been pissing me off for a while, and I'm finally trying to do something about it:
I do a lot of work with compositing as a part-time Compiz dev, so I find myself always dealing with distorted/transformed windows. The problem here is that no matter what I set in the font config tool, I can't seem to turn off true subpixel smoothing - I always get color-blended text, which looks horrible when you do things like rotate and stretch windows. Also, on a lesser note, Cairo-Dock uses the same text rendering settings, but not in the right way, leading to horrible window titles on my dock (I've tested this on two machines on which grayscale works - one running nVidia the other has FOSS ATI drivers, no problems what so ever).

This is on Intel graphics, I believe I've had the problem since Hardy (not sure, I've been on Intrepid since Alpha 2...)

Again: Intel; only have subpixel smoothing; want grayscale smoothing. Google has not helped me.

---

### Post by moomooranch on 2008-10-31
Hmm, I was able to get grayscale smoothing by inserting the code from this site:

[http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/](http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/)

into my ~/.fonts.conf file.

I'm using Kubuntu 8.10 with KDE 4.1.2 and the native desktop effects turned on.

Hope it works for you..

/mmr

---

### Post by klange on 2008-10-31
Huh. Half of that fixed it:
Needed to set "rgba" to "none" and it worked. Wonder why the font configuration tool never did it...

---

