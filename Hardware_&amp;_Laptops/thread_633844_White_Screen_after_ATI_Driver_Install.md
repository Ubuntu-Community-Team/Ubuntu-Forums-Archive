---
title: "White Screen after ATI Driver Install"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by databoy2k on 2007-12-07
Hey All:
So, in a move of brilliance, I decided to try AGAIN to install the ATI drivers (I've never managed to get them installed and working with compiz, and then get frustrated when my AWN ceases to work anyways... I love the VESA drivers). I followed the steps on the cchtml wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)), and then got to the part about "3D Desktop Effects." I did the recommended method, it resulted in a white screen, so I fixed it by uncommenting the lines that I was told to. Like an idiot, I tried the other method. 
```
mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
Hey, guess what - white screen... and now there's no "commented lines" to take out either... Now I know this is Compiz' fault because if I change my session on my login screen to a failsafe terminal, I can do different things, but I cannot boot XServer or Gnome...
So can anybody give me tips on how to fix this? Either to reverse the code that I typed or to troubleshoot and fix it?
Thanks so much everybody!
--Databoy2k

---

