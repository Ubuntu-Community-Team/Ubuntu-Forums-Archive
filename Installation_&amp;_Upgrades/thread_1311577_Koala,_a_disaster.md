---
title: "Koala, a disaster"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Kid_Sprocket on 2009-11-02
Hi Guys,

I installed Koala (having installed updates whenever mentioned or recommended by Update Manager), and am now completely unable to boot. When I do, I see a new loading screen for a couple of seconds, then the screen flashes a few different messes of green pixels, and repeat. It sometimes shows the name of my computer and the power button, and a cursor, and once I was able to actually click the power button, but within a second it flashes the green junk and restarts. 

I can get to the recovery console by selecting the second option on Grub but the screen gets jumbled, and it crashes. It says something about control+D for maintenance, but the text is all messed up, and it soon reboots.  

I'm not a Comp Sci major, but I can follow directions pretty well. If there's anything to do, I'd really like to try it. 

:(

Also, during installation, when a choice came up to keep old files or new, I kept the old. 

Maybe this is it?

---

### Post by Kid_Sprocket on 2009-11-02
To clarify: I can't DO anything from the recovery console. It just stops working.

---

### Post by Kid_Sprocket on 2009-11-02
It seems this must be a display problem.

I remembered that I had problems with one of the previous releases with the graphics.

I was able to add an option in Grub to make the display 600x800x256, and after that some mashing of function keys actually got me logged in!

Here's the weird part: my backround image was in full color, but the icons were messed up. 

Getting closer!

---

### Post by Kid_Sprocket on 2009-11-03
Okay, forcing vga, I can log in, or get to a terminal with ctrl-alt-f2.

lspci | grep VGA says I have an intel 82845G/GL chipset for video.

---

### Post by Kid_Sprocket on 2009-11-03
Wow, and it seems my sound no longer works either. 

Well, forget this. 

I'm going to download and burn Jaunty.

---

