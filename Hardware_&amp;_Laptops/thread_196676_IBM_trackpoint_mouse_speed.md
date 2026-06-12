---
title: "IBM trackpoint mouse speed"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by easy123 on 2006-06-14
It's moveing very slow and even with the sensitivity set to the highest, it still takes a lot of pressure to make it move faster. It hurts my index finger just to make the mouse move. How do I fix this?? Anyone? THanks

---

### Post by dlrider on 2006-06-19
[QUOTE=easy123]It's moveing very slow and even with the sensitivity set to the highest, it still takes a lot of pressure to make it move faster. It hurts my index finger just to make the mouse move. How do I fix this?? Anyone? THanks[/QUOTE]

I have this problem also but using Hoary.  When it gets to be too annoying I switch to a USB mouse.

---

### Post by mrpister on 2006-07-11
You can change the trackpoint settings using [configure-trackpoint]("http://tpctl.sourceforge.net/configure-trackpoint.html").

You can also change the settings via the terminal:

```

$ sudo -s
$ echo -n 168 > /sys/devices/platform/i8042/serio0/serio2/sensitivity
$ echo -n 132 > /sys/devices/platform/i8042/serio0/serio2/speed

```

Both values may be between 0 and 255. This is confirmed to work on my T43; ***your particular model may have a different path***.


References:
[http://www.thinkwiki.org/wiki/TrackPoint](http://www.thinkwiki.org/wiki/TrackPoint)

---

### Post by cb474 on 2007-01-21
The command line solution works for me. But when I shutdown and restart the new settings I created are lost. How do I get the settings to remain?

---

