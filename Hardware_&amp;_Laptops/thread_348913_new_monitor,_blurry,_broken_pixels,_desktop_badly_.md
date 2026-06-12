---
title: "new monitor, blurry, broken pixels, desktop badly configured"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by pickarooney on 2007-01-29
Just got my new monitor delivered and so far it's a massive disappointment. Four broken pixels and the screen display is all blurry, plus my desktop encroaches onto the TV display now.

Where to begin... I 'upgraded' from a trusty old 17" CRT to a 19" LCD and boosted the resolution from 1024x768 to 1280x1024. Everything is now displaying with a 'ghost' and to make it worse no matter how I choose to display my desktop image (tiled, stretched... it was previously at Tiled Maxpect), I can't get the same image on both screens - part of my PC desktop always overlaps onto the TV.

I know the pixels are simply dead and irreperable, but is there any way of fixing the blurring/ghosting or do have to write this thing off already?

---

### Post by RandomJoe on 2007-01-29
What is your refresh rate set to?  

I get some ghosting and other artifact if the refresh rate gets set to 75Hz or higher on my flat panels.  Setting it to 60Hz makes everything nice and clear.  FPs aren't the same as CRTs, so you don't get the flicker on them that you did on a CRT, which means the lower refresh isn't a bad deal.  (Although there may be some out there that are supposed to go higher now -- dunno, all mine are just 60.)

---

### Post by pickarooney on 2007-01-29
It was set to 75, factory recommendation. Tried 60 and it hurt my eyes. When a pink and white bar appeared down the right hand side and wouldn't disappear I cut my losses and put the thing back in the box.

---

### Post by jloehrlein on 2007-01-29
Out of curiosity what was the brand and model?

---

### Post by pickarooney on 2007-01-29
Nitstek (crappy no-brand) MJ9B

---

### Post by gaiterin on 2007-06-14
Hi. Try this:
Edit file /etc/X11/xorg.conf:
      /Applications/Accesories/Console
      sudo su -
      Enter your password
      cd ../etc/X11             (Care with the case!)
      nano xorg.conf

quit the not use max resolution of the standard installation, in the lines:
Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" 
Must be (in my monitor):
Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"

For exit of nano:
     Ctrl+X
     Y          For save the changes.
     Overwrite the file.
     Close the Console Window.

---------------------------
My Ubuntu start the standard configuration in 1280x1024 and 65 Hz. But I like 1024x768 y 85 Hz (the monitor not works in 1280x1024 y 85 Hz), but with 1024x768 and  85Hz, I see a error: small box pixels in the left up of the screen. With the correction up, I can see it perfect :D


Maybe try change the Default Depth color in the same file:
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Rage Mobility P/M AGP 2x"
    Monitor        "S/T 77E/76E"
    DefaultDepth    24

ponerla como Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Rage Mobility P/M AGP 2x"
    Monitor        "S/T 77E/76E"
    DefaultDepth    16

---

### Post by CrazyGuy123 on 2007-06-14
for others with the same situation:

Ghosting, to the left or right, is usually caused by an analogue VGA cable.  Replacing it with a digital DVI cable solves the problem, but if this isn't possible try checking all the connections for grub or dirt causing capacitance, or use a shorter cable and remove vga extenders.  If none of them solve the problem, you can reduce the problem by adjusting the refresh rate downwards.  That will reduce the distance between the real image and the ghost image, which makes it less noticable.  Note that contrary to experience above, this shouldn't cause flicker on LCD's.  Note, avoid refresh rates below 60Hz, as they're usually interlaced, which isn't good for LCD's.

Blurry images are caused by not having the resoloution set right.  LCD's only work well at one resoloution, so you should find this out from the manual and set it at that.  Any other resoloution will either cause blurryness, cropped edges of the screen, or a small image in the centre of the screen.

---

### Post by youbunt2 on 2007-08-19
Ya I just had the same problem but I found this thread and put my refresh rate to 60. :)
cheers! its fixed. Mines a brand new viewsonic VA1903wb 19" lcd.

---

