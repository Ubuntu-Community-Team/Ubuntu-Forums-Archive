---
title: "Problems with NVIDIA drivers"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by Kelan on 2006-12-20
Hi,
I've recently installed Kubuntu on my Toshiba laptop, but when I install the drivers for my NVIDIA GeForce4 420 Go graphics card, I get stuck in 640x480 resolution with a mysterious black bar at the right of my screen. I did some research into this, and it seems others have encountered similar problems. I tried suggested methods such as adjusting some settings in xorg.conf - which just stopped any graphics showing at all - and installing some older drivers - 1.0.4496, I think was the version. However, I was unable to compile these older drivers due to what I think was a missing 'modversion.h' header file... and from there it just lost me completely.
     If anyone has any advice, I'd be very grateful.

Thanks,
- Kelan

---

### Post by papa6 on 2006-12-20
I have the same problems with Gnome on Edgy Eft. I'll keep an eye out for a solution.

I just found this site here->[http://www.xig.com/]("http://www.xig.com/")

---

### Post by Kelan on 2006-12-20
Wow, thanks for the quick reply, papa6.
If you're having the same problem, here's a couple of sites I found earlier - maybe they will help? It seems this "black bar" is quite infamous.
Quite possibly you've already found them, but here they are nonetheless:

[http://linuxfrance.chez-alice.fr/toshiba_eng.html](http://linuxfrance.chez-alice.fr/toshiba_eng.html)
[http://www.linuxquestions.org/questions/showthread.php?t=51537](http://www.linuxquestions.org/questions/showthread.php?t=51537)

And here's one I just found: I might try it out now:

[http://forums.suselinuxsupport.de/lofiversion/index.php/t35243.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t35243.html)

BTW, I'm using the Kubuntu equivalent of Edgy Eft, if that makes any difference.

---

### Post by Kelan on 2006-12-20
It's fixed! And I'm ever so happy!
The steps on this site:
[http://forums.suselinuxsupport.de/lo...hp/t35243.html](http://forums.suselinuxsupport.de/lo...hp/t35243.html)
worked for me: I just had to adjust some bits in xorg.conf.
Yay!
Thanks for posting, papa6. Hopefully the same might work for you.

---

