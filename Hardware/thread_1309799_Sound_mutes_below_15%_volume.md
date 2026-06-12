---
title: "Sound mutes below 15% volume"
date: 2009-11-01
forum: Hardware
---

### Post by mrtymek on 2009-11-01
Hi. My sound works just fine if not that one thing. 
When I turn the volume down, at 15% I can't hear anything. It's not like it is quiet at 16% or 17%, - at this volumes I can't actually listen to music at night, cause it's too loud and when I go below 15% there's nothing but silence.

lspci gives me
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```You can probably figure out, that the driver is called Intel HD Audio.

Any Ideas?

Edit:
I am using Karmic upgraded online from Jaunty. On Jaunty the volume control was fine. Even though the vol-controll applet is different, i remember using both of them on another instalation, ant they worked fine aswell (I mean the older volume applet, and the one used in karmic)

---

### Post by geckojack on 2009-11-04
same problem, upgraded from jaunty.
lspci says:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

---

### Post by Kushkah on 2009-11-04
Check out this thread: [http://ubuntuforums.org/showthread.php?t=1309427](http://ubuntuforums.org/showthread.php?t=1309427)

---

