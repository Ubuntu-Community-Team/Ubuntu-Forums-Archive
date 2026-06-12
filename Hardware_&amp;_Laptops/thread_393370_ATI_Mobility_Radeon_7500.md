---
title: "ATI Mobility Radeon 7500"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by Hoaxe on 2007-03-25
Hi,

I'm having this little problem with my ATI Mobility Radeon 7500 graphic card that came with my laptop and how it isn't relating well to Wine.

So here is my problem: [I'm running Ubunutu Edgy btw]

```
glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```

good right? Wrong! First off, this 0x4b warninig is bothering me a lot; what does it mean? how do I fix it?

Second, I can't get a better resolution than 1024x768. But I think that is the maximum resolutin my lcd can handle, so this may not be a problem after all, but simply a limitation.

Lastly, when i run a game in Wine, it doesn't work, giving me and error that always revolvs around the fact that I can't render the 3D.

Now I understand and have looked at the many ATI threads, there are lots of problems, espcially for my unsupported version. I have faced serverX failures and been forced to reconfigure from text only modes. I have toyed long and hard with xorg.conf and I am not seeing the light.

My cards seems to work, it just doesn't work well. Beryl works and it's awesome, no doubt about that. But I fear that when it will come to any 3D game I will be faced with this lack of 3D acceleration or pixel shading errors. These all lead to game crashes on startups. Is Wine my problem? I hope someone has an answer for me. Ubuntu has been great so far and I would love to get over this graphic card problem.

thanks

---

### Post by josephus on 2007-03-25
As far as I know the warning libGL warning: 3D driver claims to not support visual 0x4b does not affect anything (at least it's on my system).

Anyway this thread helped me out a lot in getting things working : [http://ubuntuforums.org/showthread.php?t=361136](http://ubuntuforums.org/showthread.php?t=361136)

---

### Post by Xenogis on 2007-03-25
Disregard the warning. I have an LCD panel that can only do one resolution which is 1024x768 so if it is the same for you that wouldn't be surprising. Make sure your card is capable of using pixel shaders

---

### Post by Hoaxe on 2007-03-25
[http://ubuntuforums.org/showthread.php?t=361136](http://ubuntuforums.org/showthread.php?t=361136)

that is indeed a good link, i had already seen it.

My problem is really that it says direct rendering works and yet i can't play an old 3D game.

i've searched a long time for some help and followed a lot of steps but nothing seems to solve my problem.

can any of you that have the same graphic card run a 3D game through Wine?

---

