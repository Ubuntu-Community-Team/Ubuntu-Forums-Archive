---
title: "Does fglrx/catalyst support rotation? (xrandr -o left)"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by CAsurfer on 2008-02-21
Do any of the fglrx/catalyst drivers support screen rotation? The command I'd like to execute is "xrandr -o left", but I haven't had any luck.

This person claims to have gotten it working, but I was unable to emulate his results: [http://ubuntuforums.org/showthread.php?t=585856](http://ubuntuforums.org/showthread.php?t=585856)

Other posts lead me to believe it's impossible:
[http://www.rage3d.com/board/archive/index.php?t-33807057.html](http://www.rage3d.com/board/archive/index.php?t-33807057.html)

---

### Post by CAsurfer on 2008-02-24
*bump*

Anyone?

---

### Post by Cherry Cotton on 2008-03-05
The correct answer is no, sadly, and it drives me freakin' crazy. ATI has yet to implement rotation in its FGLRX driver (despite having locked up the dedicated graphics market for tablets, arrrrrgh), and Novell's open-source RadeonHD driver isn't there yet.

I'm so mad at ATI over this, I could cry.

---

### Post by oldsoundguy on 2008-03-05
NVida does support rotation .... big time! sufficient that you don't even have to open a terminal .. just go to the resolution in the system and there it is!!  (you DO have to make an entry in xorg o  .. option  .. "RandRRotation" ... "on" ... in the card device section to activate the option button on the resolution screen.)  I have 4 monitors that pivot.  Two are sharing with WinDOZE computers.

---

### Post by Cherry Cotton on 2008-03-05
Don't rub it in! :(

---

### Post by CAsurfer on 2008-04-08
I got rotation working using the open source 'ati' driver. Details here: [http://ubuntuforums.org/showthread.php?p=4680284](http://ubuntuforums.org/showthread.php?p=4680284)

---

### Post by maximAL on 2008-04-26
i followed the instructions there and the screen actually does rotate, but i get massive graphics glitches and the performance is poor (despite EXA) :(

---

### Post by Cherry Cotton on 2008-04-26
In regard to poor performance: in order to get EXA working, you may need to build the latest DRI (Direct Rendering Infrastructure) from its Git tree. Instructions on that here: [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)

In regard to graphics glitches: Awwww, man! I'd guess it's a driver bug (at least, that was the case for some time when I had a big black stripe on my screen when rotated). You might want to post a bug at the driver's bug tracker, or see if there's one already there: [https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=xorg&content=radeon](https://bugs.freedesktop.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=xorg&content=radeon)

I hope that helps!

---

### Post by maximAL on 2008-04-28
so, as the mesa build fails and i am **not** going to build X11 and a loads of other stuff myself: will it work with nvidia cards properly?

---

### Post by CAsurfer on 2008-04-28
I had a computer with an nVidia GeForce 5200, and rotation worked flawlessly. It was a while ago, so I didn't try Compiz with it. I think I used the proprietary driver, and got it working like this: [http://ubuntuportal.blogspot.com/2007/02/how-to-setup-pivot-screen-rotation-with.html](http://ubuntuportal.blogspot.com/2007/02/how-to-setup-pivot-screen-rotation-with.html)

---

