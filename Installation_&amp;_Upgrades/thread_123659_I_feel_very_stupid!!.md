---
title: "I feel very stupid!!"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by jazzinsa on 2006-01-30
I cant beleave how stupid i feel. I'm on pc's loooong before windows ever dreamed of being a window and I know pc hardware pretty well. Now i've flipped to ubuntu and whalla, I know nothing.

Can someone please explain what to do after i've upgraded my screencard. 
was: ATI All-in-wonder pro
now: MSI nVidia FX5200

I can get to terminal screen but dont have a clue what to type in.

---

### Post by kaamos on 2006-01-30
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```
You should be able to configure you display settings from there.

---

### Post by ddtmsa on 2006-01-30
I'd had both Unix and Windows experience, and also felt very stupid when first trying to set up Ubuntu. I also have an nvidia FX5200 card, which I added after installing Ubuntu. After doing the re-configure script already suggested, it now works perfectly well! For other information about this and many other topics have a look at 

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

which mentions how to install the nvidia drivers.

---

### Post by jazzinsa on 2006-01-30
Thanks a lot dudes... I will try that!

---

