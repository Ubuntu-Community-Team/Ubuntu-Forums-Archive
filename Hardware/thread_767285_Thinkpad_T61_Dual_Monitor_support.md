---
title: "Thinkpad T61 Dual Monitor support"
date: 2008-04-25
forum: Hardware
---

### Post by shortarabguy on 2008-04-25
Hey, sorry if this has already been covered, but I couldn't find anything specifically related to my problem...

I'm using a Thinkpad T61 with integrated Intel video card, and I'm trying to attach an external monitor. So far so good, but the monitor just clones the original screen. I can even make the resolution 1920x1200( the size of the external) through the Resolution interface in System-->Preferences, but that just makes the notebook monitor 1920x1200 as well( except zoomed in, so I only see a small portion of the screen on that display).

My question is how to make the display extend from the original rather than clone it in any way. I've seen methods for doing this with the nVidia chipset, and the method involving Xinerama, but I'm not using a dedicated card( excluding the first solution), and I was hoping for a solution that wasn't so... well, confusing.

Thanks for your help.

---

### Post by russlar on 2008-04-26
I'm having a similar problem. I've got a T61 with an Intel GM965 graphics card, and an LCD hooked up to the DVI port on a docking station. The built in display works fine, however the external LCD does not display. It is detected by the Resolution utility, but will not display, cloned or otherwise. Every solution I've found deals with nVidia cards.

I tried the 7.10 live CD, and it displayed fine, but 8.04 installed to my hard drive (via wubi) will not output to external LCD.

I'm wondering if anyone else has a solution/workaround to this. Should I just copy the xorg.conf from the live cd and use it in place of the xorg.conf that installed with 8.04?

---

### Post by Wej on 2008-04-26
> **shortarabguy said:**
> Hey, sorry if this has already been covered, but I couldn't find anything specifically related to my problem...

I'm using a Thinkpad T61 with integrated Intel video card, and I'm trying to attach an external monitor. So far so good, but the monitor just clones the original screen. I can even make the resolution 1920x1200( the size of the external) through the Resolution interface in System-->Preferences, but that just makes the notebook monitor 1920x1200 as well( except zoomed in, so I only see a small portion of the screen on that display).

My question is how to make the display extend from the original rather than clone it in any way. I've seen methods for doing this with the nVidia chipset, and the method involving Xinerama, but I'm not using a dedicated card( excluding the first solution), and I was hoping for a solution that wasn't so... well, confusing.

Thanks for your help.

I am having the same problem with my Dell Latitude D520 with the Intel 945 graphics chipset. I am using my large screen, but no matter how I drag my monitors around in the new resolution editor and no matter how many times I hit the key combination to switch between LCD/CRT on the keyboard, it still just clones the desktop and cuts off 80% of the screen on the laptop. If I check the clone desktop button it clones the 1024x768 resolution/screen to both monitors, which is to be expected, but unchecking it doesn't fix it.

---

### Post by gsalem on 2008-05-18
If you haven't solved this yet, have a look at
[intel linux driver]("http://www.intellinuxgraphics.org/dualhead.html")

---

### Post by dangermouse28 on 2008-05-20
Have you tried urandr? It works with both Intel and ATI graphics chips. Takes all the hard work out of using external screens and projectors with laptops!

---

### Post by samskpun on 2008-06-22
i have a 24 inches external and 15 inches T61. It took 5 second to configure it with urandr

urandr, 
[http://www.albertomilone.com/urandr.html](http://www.albertomilone.com/urandr.html)

---

