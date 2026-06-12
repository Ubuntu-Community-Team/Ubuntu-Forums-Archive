---
title: "laptop lcd brightness controls reversed"
date: 2008-09-21
forum: Hardware
---

### Post by gl2tosl2 on 2008-09-21
I have a lenovo sl400.  The brightness controls are reversed.  If I use the lcd brightness applet in gnome, what it thinks is 0% is bright, and 100% is dark.

The brightness keyboard keys also misbehave.  Brightness down sets the brightness as 20%.  Brightness up sets brightness to 25%.

Lastly, cranked all the way to bright (inverted for the gnome applet) only gets me to 85%.

All of these percents are coming from 
/proc/acpi/video/VGA/LCDD/brightness 
e.g.
```

leif@peacock:/etc$ cat /proc/acpi/video/VGA/LCDD/brightness 
levels:  100 90 85 80 75 70 65 60 55 50 45 40 35 30 25 20
current: 85

```

---

### Post by maxitaxi on 2008-10-03
Hi, I just got an SL400 too. I'm having the same issue. The brightness is reversed in Gnome. It's odd, because the computer, after a period of inactivity switches into a brighter mode!

It's definitely limited too, doesn't go beyond 85.

What you can do is set brightness to 100 by typing:
```
echo 100 | sudo tee /proc/acpi/video/VGA/LCDD/brightness
```

But hopefully this will be fixed. What is a good place to report this as a bug?

---

### Post by gl2tosl2 on 2008-10-04
That command lets me get to all of the brightness levels.  

Updates since my original post have improved the behavior of the brightness control.  Now they cycle from 25% to 85%.  I haven't checked each level, but it seems like they are using the brightness steps shown above.  But the direction is still reverese.  I.e., "brightness down" makes the actual brightness go up.

maxitaxi, do you have the volume control buttons working?

---

### Post by maxitaxi on 2008-10-05
No improvements with LCD brightness.

> 
maxitaxi, do you have the volume control buttons working?


Volume control buttons also don't work at this point. I have other issues too, so I made a thread trying to gather some attention to them. See the thread [here]("http://ubuntuforums.org/showthread.php?p=5912609#post5912609").

Cheers,
Max

---

### Post by Changturkey on 2008-11-29
Another SL400 user here, having the same problems..

---

