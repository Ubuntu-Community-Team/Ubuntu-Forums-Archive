---
title: "Latitude XT trackpad not detected"
date: 2009-04-10
forum: Hardware
---

### Post by m3pz on 2009-04-10
My Dell Latitude XT trackpad (an Alps model) isn't being detected as a trackpad. /proc/bus/input/devices lists it as a "PS/2 Generic Mouse", and consequently anything in userspace refuses to believe it is a trackpad (meaning I can't use configure it using gsynaptics, etc.).

I was on Intrepid, and then I upgraded to the Jaunty beta, but to no avail.

Has anyone had experience with a similar trackpad problem, or got their trackpad on a similar Dell model working?

Thanks!

---

### Post by Keeper of the Keys on 2009-04-19
It seems from this page that the regular synaptics driver should work:
[http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77](http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77)
Good luck...

---

### Post by m3pz on 2009-04-19
Thanks for the reply. I know the Synaptics driver should work, but my system has no chance to use it since it's detecting the touchpad as a PS/2 Generic Mouse.

My question then, I guess, is how do I force it to detect it as a Synaptics touchpad?

---

### Post by gohanssjn on 2009-05-02
Same problem here.

---

### Post by gohanssjn on 2009-06-30
Ever find a solution?

---

