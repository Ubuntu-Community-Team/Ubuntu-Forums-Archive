---
title: "Mouse stuck in 'alternate' click on ibook g4"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by justrust on 2006-11-20
This is my first forum post in any forum ever.  food for thought.

anyway, i just got ubuntu onto my ibook (g4, 1.42ghz ppc), and it was all going fine for a while.  then i went to customize the mouse movement, and after playing with the light bulb in the 'double click' test area, i suddenly had no primary mouse button functionality.  it just alternate clicks everything (not sure it its button 2 or 3 or what, since i only have one button on this thing).

so i cant click anything at all anymore without getting an alternate menu (context menu i think its called?), which is pretty drnd limiting.

in case it matters, yesterday after first installing, i followed the directions on this post: ([http://www.ubuntuforums.org/showthre...+slow+trackpad](http://www.ubuntuforums.org/showthre...+slow+trackpad)) because because my mouse used to be amazingly slow.  i pasted the code into xorg.config, and deleted the other 3 incarnations of those settings (for some reason also, the mouse settings were repeated 3 times before).

so i cant do any more work on this thing until i can use my mouse!  any help would be greatly appreciated

thx

---

### Post by justrust on 2006-11-24
boy do *i* feel silly.  i had accidentally turned on the 'left handed mouse' option while customizing the mouse (thanks to that blasted tap-to-click functionality).  so all it took was a three fingered tap and i was able to change the setting back.

as a side note, i had some trouble finding out how to turn off tap-to-click option, but in the end just edited the /etc/X11/xorg.conf file, and set the line 

```
Option "TapButton1" "1"
```

with

```
Option "TapButton1" "0"
```


...its lonely being the sole reply to your own first post :oi

although to be fair, in retrospect, the question was pretty stupid.

---

