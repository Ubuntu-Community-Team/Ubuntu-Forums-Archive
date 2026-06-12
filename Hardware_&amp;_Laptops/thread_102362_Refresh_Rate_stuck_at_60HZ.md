---
title: "Refresh Rate stuck at 60HZ"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by Speedyz2 on 2005-12-11
Hey guys,
   I've seen numerous psots on this and have seen how to fix this. The only problem is that I'm using a laptop and do not know what my Horizontal + Vertical Sync are to be able to be safe. I know I was running it at 75hz when I had windows though and would like to turn the resolution to 1152 x 864 @ 75hz, but don't want to risk damaging my laptop monitor. If you guys could help me with editing my xorg.conf file so that I could get 75hz I would be greatful. Yes I ran the reconfigure, but without knowing what my Syncs are I could mess up my laptop......I searched my manual and internet but couldnt find it. I have a Gateway 600series(600YGR/YG2 to be more specific). Thanks for any help guys!

---

### Post by frodon on 2005-12-12
If you don't have your hsync and vertsync parameters you should call or send an email to the manufacturer in order to get them, it's really the best way to solve all your resolution problems.
However if you can't do that, there is 2 way :
1- You could try to add a modelline if you know a resolution you want that your screen can handle. See this thread for details on how to add a model line : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
2- Post here the full name of your laptop and we will try to find someone who have the same laptop in order to get the hsync and vertsync parameters.

---

### Post by Speedyz2 on 2005-12-12
Thanks,
   My exact model is a Gateway 600YGR. It's a laptop so I'm nto sure on the syncs. When i check my xorg.conf and look under monitor is says Default monitor   and there are no Hsync or vertsync specified..... If anyone can be a help i'd appreciate it. Thanks.

---

### Post by bored2k on 2005-12-12
Have you tried
```
sudo dpkg-reconfigure xserver-xorg
``` and reboot ?

---

### Post by mlomker on 2005-12-12
[QUOTE=Speedyz2]If anyone can be a help i'd appreciate it. Thanks.[/QUOTE]

Just try a line from a modeline generator (frodon gave you a good link).  If it isn't within range then you end up with a black screen, that's all.  I wouldn't bother, personally, because it's a lot of trial-and-error but if you have the time to kill...

---

### Post by Speedyz2 on 2005-12-13
cool...thx guys, i tried the xserver reconfig, but without knowing my hsync and vsync its pretty usless. ill try the modline generator though. thnx guys for the help.

---

