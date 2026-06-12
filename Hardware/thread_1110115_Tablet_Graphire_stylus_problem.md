---
title: "Tablet Graphire stylus problem"
date: 2009-03-29
forum: Hardware
---

### Post by jrrpnani on 2009-03-29
In my previous post I told that I have two problems with my Graphire Serial tablet. 
My second problem it's about the stylus. 
When I use the stylus in the Gimp program, and I draw with the pencil, for example, I obtain this result  I have marked the point with red arrows.
[IMG]http://web.madritel.es/personales2/jrramos/test.png[/IMG]
  
You can observe greatest size points along the plotted path. It's like paint the maximum size of the brush, every x time. 
I have included in the Xorg.cfg parts like; 
 
Option "PressCurve" "50,0,100,50" # Custom preference 
Option "Threshold" "5" # sensitivity to do a "click" 60 
Option "HistorySize" "64" #Taille buffer 
Option "Speed" "1.0" 
 
But I have obtained any result.

I'm using Ubuntu 8.04

---

### Post by Favux on 2009-03-29
Hi jrrpnani,

It sounds like you are doing most of your calibration through xorg.conf.  Have you used the linuxwacom calibration tool wacomcpl?  If you installed wacom-tools you should have it.  You type "wacomcpl" and it pops up.  It will create a hidden file called .xinitrc in your /home/username/ directory.

The .xinitrc applies after xorg.conf.  So it's settings will control.  I think the problem may be your presscurve settings are a little extreme.  Maybe try something like:  10,15,85,90

If you want to use wacomcpl and have .xinitrc apply each time you boot go to section 3 here:

[http://ubuntuforums.org/showthread.php?t=1038949]("http://ubuntuforums.org/showthread.php?t=1038949")

I hope this is helpful.

---

### Post by jrrpnani on 2009-04-02
I want to try the link that you post me. When I have done, I told  you about the results.

Thanks

---

### Post by jrrpnani on 2009-04-04
I have tried different configurations option with wacomcpl. But don't solve the problem. I feel the changes in the stylus (velocity, pressure...) but anyone avoid this greater points in the trace line. 
I gonna still trying. :(
One thing that I solved with your link post, it's the problem with the buttons of the Wacom mouse. Thanks anyway. ;)

---

