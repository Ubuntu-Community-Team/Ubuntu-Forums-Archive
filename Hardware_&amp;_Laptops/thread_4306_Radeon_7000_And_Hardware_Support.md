---
title: "Radeon 7000 And Hardware Support"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by Mirak on 2004-11-13
I HAVE AN ATI RADEON 7000 64MB AGP 4X VIDEO CARD

i was wondering if there is any way posible for me to get hardware support with this card, if any...

i am using warty atm, but hoary will work fine for me, i am not sure of xorg, i never got that installed, (i break my X, trying out different drivers and such, and have to re-install, as i am not able to fix it). i am about a month and a half to 2 month old newb, (using linux for that period of time, duh!). but not an idiot, just take it easy on me

just any support would be great, i guess.      and my reason for this, or i guess, testing situation, would be enemy territory,

thanks in advance

---

### Post by Mirak on 2004-11-13
Just An Update
i am now on hoary, and using Xorg, still with the default ubuntu ati driverse, and a default xorg settings file (xorg.config?)
fps is a bit lower now, like 2.5k+ instead of 4k+
but now i get no errors, or messages when i run glxgears, it just stats spitting fps lines................howcan i tell if i am getting 3d hardware support?

---

### Post by Magneto on 2004-11-14
[QUOTE=Mirak].howcan i tell if i am getting 3d hardware support?[/QUOTE]

look in /var/log/XFree86.0.log or the xorg variation of that log in the same place

it will show you the results of X loading

support in xorg for Radeon sucks try google and look up xorg and radeon 7000 - xorg's ati issues are well known

---

### Post by Viro on 2004-11-14
In a terminal, type glxinfo. If it says "direct rendering :yes" among all that stuff it outputs, you've got 3D hardware acceleration.

---

### Post by Mirak on 2004-11-14
hmmm, well, i was told by ogra on #ubuntu that i am using Xorg, but when i run ET the output from that says it loads Xfree stuff, and now i dont have sound from ET, cant find the device or something, and glxinfo gives like a chart, but notjhing like ou mentioned, 

should i go back to Xfree, and try my luck there, or am i screwed regardless


hmm, maybe i should just get an nvidia card, can you guys think of an nvidia equivalent to a ati radeon 7000 64mb agp4X, for around 40 bucks?

oh yeah, something that i have a chance to get 3d on would be great

---

### Post by HiddenWolf on 2004-11-14
You won't be able to get hardware accel under x.org on any radeon card untill ATi releases it's next set of drivers, rumored to be out in december.

---

### Post by Viro on 2004-11-14
[QUOTE=HiddenWolf]You won't be able to get hardware accel under x.org on any radeon card untill ATi releases it's next set of drivers, rumored to be out in december.[/QUOTE]
 You don't need the official ATI drivers if you want 3D acceleration with chips below the Radeon 9500 range. That means that ATI Radeons 9200 and below can have hardware acceleration with the stock drivers that come with XOrg and XFree86. Check out the DRI project for more information.

---

### Post by glmeece on 2004-11-18
I have the exact same card, but I *do* have acceleration. Take a look at this post for some pointers as to how I got my acceleration restored (I had it, but lost it when I attempted to apply the newer ATI drivers):
  [http://www.ubuntuforums.org/showthread.php?t=4343]("http://www.ubuntuforums.org/showthread.php?t=4343")
  
  If that doesn't get it for you, let me know.
  
  - Greg

---

