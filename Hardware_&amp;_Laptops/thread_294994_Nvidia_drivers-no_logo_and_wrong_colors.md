---
title: "Nvidia drivers-no logo and wrong colors"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by tymek666 on 2006-11-07
I've installed nvidia glx drivers from repos, changed nv to nvidia in xorg.conf file. It works great since 5.04, but 6.10 xserver doesn't load nvidia driver at startup. I think that because theresn't nvidia logo and wallpaper colors are reduced.
However, when i restart xserver, logo apears and colors are fine.
So i have to restart xserver every time. I've checked xorg.conf file but everything seems to be ok.
Do you have an idea how to fix it?

---

### Post by PrinceArithon on 2006-11-07
Basically what you might want to try is this.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)


The only thing I suggest is don't type in thefuture unless you feel like playing around with something very interesting.

Anyway when I did this it allowed me to work with the nvidia driver instead of nv....that damn nv really causes a lot of problems.

And if that doesn't work for some reason, then try this one 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

These are all the things I have ever used and it works well.

I suggest you look through the entire wiki and try everything you want.  This thing is really nice and I have to say it's helped me learn a lot as well as move away from Windows almost completely.  The only time I really do use Windows is at work or school.

---

### Post by tymek666 on 2006-11-08
I know how to install nvidia drivers and i know what's Wiki ;)
But i don't understand why i have to restart xserver every time to get this drivers works. I've installed these drivers many times and always worked fine. Until 6.10....

---

