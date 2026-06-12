---
title: "Black Screen"
date: 2015-10-06
forum: Hardware
---

### Post by cranerja on 2015-10-06
I am currently encountering a black screen when starting ubuntu 14.04 on a GTX770 with the 341 (now 355) drivers connected to a SEIKI SE39UY04. I have ran all the black screen instructions and instructions for SEIKI with nvidia. This only started today, whereas it was running just fine for a year or so. One thing that troubles me is that xrandr gives me the error "Can't open display". This happens with xrandr, xrandr -d :0 -q, and xrandr -d :0.0 --verbose. What would cause xrandr to fail like this?

---

### Post by v3.xx on 2015-10-07
Did you have a kernel update?

If so, try going back to previous kernel.

---

### Post by cranerja on 2015-10-07
> **v3.xx said:**
> Did you have a kernel update?

If so, try going back to previous kernel.

No, nothing was updated before the occurrence. Thank you though

---

### Post by efflandt on 2015-10-08
What do you get for:```
uname -a
dpkg-query -l nvidia* | grep ii
```Are you using graphics-drivers/ppa, because graphics drivers are no longer on xorg-edgers/ppa? I have nvidia-355 (355.11) on my 14.04 laptop and desktop and it generally works fine. However, after my graphics has been in standby (I don't suspend or hibernate my system) and I log back in from locked screen, there seems to be some graphics corruption of top bar and Unity bar of my desktop (GTX 750 Ti). But hovering over the top bar clears that up or clicking on any app in the Unity bar clears it up. Other than that it works fine for Steam games and graphics tests other than peculiar slowness the first time I benchmarked my laptop (worked fine after rebooting): [http://openbenchmarking.org/result/1510079-BE-1510047BE83](http://openbenchmarking.org/result/1510079-BE-1510047BE83)   (may need to click on that 2nd time if 1st time redirects to their main page).

---

