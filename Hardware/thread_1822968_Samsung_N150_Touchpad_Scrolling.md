---
title: "Samsung N150 Touchpad Scrolling"
date: 2011-08-11
forum: Hardware
---

### Post by Captain NFB on 2011-08-11
I have just got a Samsung N150, and installed Natty. Everything worked OOB, except the touchpad scrolling. I looked in the touchpad control panel and the 'Enable vertical Scrolling' was checked. At this point I checked 'Enable horizontal scrolling', which resulted in horizontal scrolling working, but still no vertical scrolling. 

I then searched on the forums and found this link:

[http://superuser.com/questions/136568/get-back-the-touchpad-scrolling-missing-in-kubuntu-10-04](http://superuser.com/questions/136568/get-back-the-touchpad-scrolling-missing-in-kubuntu-10-04)

Where Patches and Richard Flynn (I'm not sure which) posted this solution:

Just found this, which works in Ubuntu. Open a terminal, and type in the following lines:

```
sudo modprobe -r psmouse
```
```
sudo modprobe psmouse proto=imps
```

This enables scrolling for your current session - test and make sure it works. If so, you can make it permanent by:

```
sudo gedit /etc/modprobe.d/options
```

and adding the line:

```
options psmouse proto=imps
```

Then close and reboot.

I followed these instructions and now have vertical scrolling.:D But not horizontal scrolling.:( 
The touchpad control is now a mouse control with no touchpad tab and no 'Enable horizontal scrolling'.
Does anyone know how to get both horizontal AND vertical scrolling at the same time?

---

### Post by ranjank on 2011-08-11
Even I have the similar problem. I can't do two finger scrolling. Only option to scroll for me from touchpad is dragging scroll bar. MIne is Samsung NC108-A4IN

---

### Post by fidelandche on 2011-08-12
I have the same problem with my N150 plus, it appears if you are using Chrome there is an issue with scrolling, vertical scrolling in firefox works well.

Cheers

---

### Post by last.try on 2011-10-19
Oneiric Ocelot. N150. Same trouble :(

---

### Post by hit on 2012-02-07
Wow! I finally got scrolling working with this solution. And by scrolling I mean 'normal' scrolling, not this jumpy stuff I had before. Thank you!

---

### Post by mclx on 2012-02-23
Merci Captain NFB for the solution, it works perfectly. It is so nice to be able to scroll without everthing going madly up and down  !

---

