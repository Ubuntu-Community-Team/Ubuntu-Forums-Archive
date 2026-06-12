---
title: "7970m constantly under load"
date: 2013-04-06
forum: Hardware
---

### Post by phYnc on 2013-04-06
Currently on a fresh install of 12.10 with Unity and the newest 13.3 beta 3 catalyst driver. But even when on the desktop with no programs open it seems to be idling at 25-30% GPU usage and 47-51**°**[B]C. 

[/B]```
[COLOR=#000000][FONT=Ubuntu Mono]aticonfig --odgc --odgt [/FONT][/COLOR]
```

Screenshot: [http://i.imgur.com/VsmrAXA.png](http://i.imgur.com/VsmrAXA.png)

Can anyone explain? Is this normal / how can I fix it? 

The only thing I can think of is compositing but that seems rather high GPU load just to composite? I'm still fairly new to linux, dipping into it on and off.


**EDIT 1** =  Installed xubuntu-desktop and it idles at 25% load. But I then disabled compositing and it idles at 0-1%. It seems that compositing is actually using over a quarter of the GPU usage on a high end mobile card.

**EDIT 2** = Unity - Cinnamon - Cinnamon 2D - Gnome3 Classic (suspended effects) all seems to idling the GPU at 10-25% load. So far only XFCE seems to actually idle at 0-1%

---

