---
title: "Logitech QuickCam Express (046d:092f): Blue Hue"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by TheAberrant on 2007-05-13
Hi all,

   Getting an issue with my Logitech QuickCam express (046d:092f in lsusb) where in Camorama my colors are all in a blue hue.  I haven't seen any issues like this anywhere, other than a post about inverted colors.  Anyone have any ideas?  I tried recompiling my kernel based on [Spca5xx]("https://help.ubuntu.com/community/Spca5xx"), only using the updated driver from the website mentioned, and not doing some things that didn't seem to need to be done (though I may of been wrong).  Any ideas?  I can grab extra logs if need be...

 Thanks

---

### Post by jjordan on 2007-05-14
Not trying to be a smart-a--, but have you tried adjusting the hue in the video adjustment dialog?

-j

---

### Post by TheAberrant on 2007-05-14
> **jjordan said:**
> Not trying to be a smart-a--, but have you tried adjusting the hue in the video adjustment dialog?

-j

Haha, yeah, tried that - but didn't do anything.  I'm not at the system right now, but will be checking some things I saw regarding settings when I get home.

   Thanks

---

### Post by funkenstein on 2007-05-16
hey there, I'm getting the same issue on FF7.04, you found a solution yet? (I got the 0920 QC Express)

---

### Post by funkenstein on 2007-05-27
crazily enough, having installed ubuntustudio 7.04, the webcam works fine (apart for how it's zoomed in on my forehead...)

---

### Post by TheAberrant on 2007-05-28
> **funkenstein said:**
> crazily enough, having installed ubuntustudio 7.04, the webcam works fine (apart for how it's zoomed in on my forehead...)

Interesting - I'll try to install that tonight (though I've been using my work WinXP laptop more since WoW is broken on WINE with my ATI card - another thread entirely).  I'll post if it works - if so I'll investigate to see the differences.

---

### Post by funkenstein on 2007-06-03
... so no idea about how not to have the camera zoomed in on my face then?? :P well, I'll carry on hunting...

---

### Post by bdonkey on 2007-06-19
In normal feisty fawn 7.04 (not ubuntu studio), I fixed it by adding

```
options gspca force_rgb=1
```

to /etc/modprobe.d/options while using the [http://mxhaard.free.fr/](http://mxhaard.free.fr/) drivers.

---

### Post by argotnaut on 2007-06-20
That fix worked for me in camorama, but nowhere else. :(
(Logitech QuickCam Communicate STX)

---

### Post by tdrusk on 2008-03-12
it happens when you automatically adjust colors.

---

### Post by Hunne on 2008-04-21
go into camorama and then add the Effect "Color Correction". I also have the STX

---

