---
title: "Problem starting Ubuntu 7.10 (Gutsy Gibbon) Beta in &quot;Graphics Safe&quot; mode on T61p."
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by zeyda on 2007-10-07
Hello friends,

I recently acquires a Lenovo T61p and am very keen (not to say desperate) to get Ubuntu 7.10 (Gutsy Gibbon) installed on it (asap). I looked at some posts and contributions pointing out issues with the previous Feisty release and the T61p, however after reading, for example,

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61")

I was confident there shouldn't be any insurmountable problems. Gutsy also seems the best option in order to support the newer hardware, etc.

What I am a little confused about is that even in "Graphical Safe Mode" the Beta release of Gutsy (downloaded from [http://releases.ubuntu.com/7.10/]("http://releases.ubuntu.com/7.10/")) wouldn't completely boot up on my machine, as mentioned before it's a Lenovo T61p (TYPE 6460-6YB, S/N L3-A7539 with NVIDIA Quadro FX 570M graphics adapter).

Essentially the start-up procedure gets stuck when the GNOME Display Manager is started, the screen switches for the fraction of a second but shuts down immediately. This repeats about 5 or 6 times, then the system seems to give up. The following lines are displayed on the bottom of the screen:

* ...
* Starting GNOME Display Manager...
* Starting deferred execution scheduler atd
* Starting periodic command scheduler crond
* Running local boot scripts (/etc/rc.local)

Nothing happens afterwards..

I would suppose that even with the new graphics hardware of the T61p Ubuntu Beta should start up in Safe Graphical mode?! As mentioned, Tribe 5 of Gutsy does so.

If this is a duplicate of some issue already posted apologies -- I'd be grateful for more information. Clearly I would be hoping that a similar problem might not arise with the final release due shortly, any light shed into this would be great.

Many Thanks,
Frank

---

### Post by smartboyathome on 2007-10-07
Try Gutsy Final when it comes out. The Gutsy Beta disc is kind of out of date now (many, many packages have been upgraded), and it might have been fixed already. It comes out in a few days, remember!

---

### Post by flexion on 2007-10-18
same problem still exists with 7.10 **final** here on the T61p with nvidia card. 
normal and safe graphics mode both fail to load the desktop for installation from livecd :-( 

the last CD before RC1 was released, was booting fine! RC failed to boot and now final release as well

 :confused:

---

### Post by tonyric on 2007-10-18
Use the alternate install cd. I was hoping that Xorg/NVidia would have had the nv driver fixed by now but I guess not. SIGH

---

### Post by flexion on 2007-10-19
good news! 
thanks to [this post (link)]("http://ubuntuforums.org/showpost.php?p=3566807&postcount=16") I was able to boot from livecd in order to start the installer on the T61p! 
boot in safe graphics mode, then switch to a console and startx manually..  odd, but it works ;)

---

### Post by zeyda on 2007-10-21
> **flexion said:**
> good news! 
thanks to [this post (link)]("http://ubuntuforums.org/showpost.php?p=3566807&postcount=16") I was able to boot from livecd in order to start the installer on the T61p! 
boot in safe graphics mode, then switch to a console and startx manually..  odd, but it works ;)

Many thanks for this pointer, that solved the problem for me too.

It might still be worth to investigate why the X display doesn't start automatically on the T61p (or otherwise immediately terminates), one for the next release I suppose..

Cheers,
Frank

---

