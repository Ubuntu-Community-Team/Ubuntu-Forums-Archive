---
title: "Intel 965 X3100 Drivers"
date: 2008-07-30
forum: Hardware
---

### Post by mpiskorz on 2008-07-30
Good day,

I've been looking over many posts and doing many google searches and I have not found a solution to my issue.  Hopefully someone can point me in the right direction.

I have a laptop with an intel X3100 graphic card in it.  I would like to be able to use a second monitor for an extended desktop.

I've looked at the intel driver website and ran the 3 git commands.  
Question:  do I need to do anything after I have done that?  I have tried ./configure and make install but I get an error on both commands.

I have tried to change my xorg.conf in the device section to be "intel" but that did not work either.

When I run this: gksudo displayconfig-gtk  I see that I have two driver sections and they both point to the vesa driver.  I even tried to use the i810 driver by selecting Intel and 965 from "Choose driver by model" wizard in the displayconfig-gtk.  That seemed to do something because now when I start I get the low-resoltuion error message in X.

I also tried to remove the vesa driver(xserver-xorg-video-vesa
) once I had installed the intel driver (by apt-get install xserver-xorg-video-intel ) but that only caused a text login screen to appear.

From other posts, I found this site [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

and tried to run it.  It tells me that the vesa driver is definitely in use. 

lspci | grep VGA returns:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)


So... what am I doing wrong?  I don't even care what driver I use  if I could just extend my desktop.  

Thanks for taking the time to look at my post.
Matt

---

### Post by MikeandLiz on 2008-08-09
I have the same problem, I stumbled upon this website that might prove to be useful [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html) let me know how it goes for you. I've got super slow internet where I am right now but will let you how it goes. Tell me if you make any progress with it!

---

### Post by Juhla Mokka on 2008-08-28
> **MikeandLiz said:**
> I have the same problem, I stumbled upon this website that might prove to be useful [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html) let me know how it goes for you. I've got super slow internet where I am right now but will let you how it goes. Tell me if you make any progress with it!
Looks like he's tried it:
> I've looked at the intel driver website and ran the 3 git commands.
Question: do I need to do anything after I have done that? I have tried ./configure and make install but I get an error on both commands.


I have the same problem with the same card and found the Intel download site as well, but when tried to install the file, *no makefile (or something like that) came up and could not install.

**Would there be any other solutions?**

---

### Post by Juhla Mokka on 2008-08-28
I noticed that **Direct rendering: No** and that is a problem, is it?

However, compiz-check (mentioned in the first post) tells that rendering is done by Xgl.
But what's GXL which I have? I am confused.

---

### Post by Juhla Mokka on 2008-08-29
Mine is now working (at least much better than before). Compiz-check result is different: first it skipped the first two checks and gave warning for the last. Then it gave me the option (y/N) to alter blacklist, which made the last option to return OK. Now running it again after reboot, it returns OK for all.

At first, it told me that rendering was done by Xgl.
Now it's working, and tells it's dobe by AIGLX.
Command gksudo displayconfig-gtk tells that vesa driver is still in use.


I do not know exactly what I did to make it work. When I reeboted this am, it was ok.
[COLOR="Blue"]Maybe somebody could explain?[/COLOR]

---

