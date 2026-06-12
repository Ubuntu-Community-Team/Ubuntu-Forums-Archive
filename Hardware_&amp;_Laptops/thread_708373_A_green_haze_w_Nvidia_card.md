---
title: "A green haze w/ Nvidia card"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by David_Nicoson on 2008-02-26
What do you suppose this haze is?  I thought maybe it was a color-space conversion issue, so I dorked around with the color depth to no avail.  This is the Nvidia binary driver, but I get the same thing with the open-source one.

It's not a cabling issue or a physical defect of the monitor.  (It works OK in windows and an older version of Knoppix, and as you can see I'm vnc'ed into the machine in question and seeing the effect.)

I tried running Envy, but that makes things much worse.  (Half the screen is a solid color.  I can't discern any text.)  

Any other ideas?

[img]http://i103.photobucket.com/albums/m123/bigdavex/haze.jpg[/img]

---

### Post by TheLions on 2008-02-27
check you monitor cable, it seams that you have a pin broken or curved!

if the cable is OK, try with vesa driver...

---

### Post by David_Nicoson on 2008-03-03
I turned off subpixel smoothing for the fonts, which makes the text much better.

The graphical elements still have a few stray green pixels around them.

---

### Post by TheLions on 2008-03-04
try running this in terminal:

```
nvidia-settings
```

an in setcion " **X server color corection** " put brightness and contast to 0 and gamma to 1

---

### Post by sytemlord001 on 2008-06-12
Ok so i also have the same eror and i tried changing the settings to what the guy above said. But the eror seems to persist. Although it might be a bit less visisble now.

Are there any other sujestions for settings i can change? I am pretty sure i have the best possible drivers installed for my GIGABYTE NVIDIA 8600 GT. 

I can put on all effects of compiz. Only in the lowest graphics setting there are almoste no green pixels.

I also noticed the the green pixels tend to come up over black areas and selected area's. Since most text is black moste of the text on my screen is black or green (depending on if the error has already kicked in on that area).

I realy don't know how to solve this problem, i am past the idea that it is a graphics driver since i have been installing and uninstalling drivers for about a week and i always get the error. 

Anyway thx for looking in to this... any hint could help.

---

