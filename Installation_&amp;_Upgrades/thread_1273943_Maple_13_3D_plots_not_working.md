---
title: "Maple 13 3D plots not working"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by tom.swartz07 on 2009-09-24
Hi everyone,

I recently installed maple for use with my upper level calculus course and to help with my physics research.

One main use is the 3d plots. Earlier today I tried to plot a simple 3d equation, and ended up with this incorrect result. [IMG]http://lh4.ggpht.com/_tORug_uHNu4/SqhnImLducI/AAAAAAAAAG0/zbAjqjKw5-8/s400/1.gif[/IMG]


I have a strong reason to believe it is because my graphics card is either not interfacing with the program, or it isnt even setup correctly.


I have an ATI Radeon x1270 card, and have decent performance with desktop effects, so Im not sure that it is the card itself that isnt working, I think it may be Maple not working with the card.

Did anyone come across a similar problem, and if so, is there a way to fix this?
Like I said, I will need the use of Maple for my classes and research, so the sooner I could fix this, the better!

Thanks!!
Tom

---

### Post by bdEVILord on 2009-11-03
I have the exact same problem (and in the same situation too). I'm running Ubuntu 9.10 on a laptop with a Mobility Radeon 9700. All desktop effects are working and run smoothly.

---

### Post by cb951303 on 2009-11-03
did you try disabling desktop effects?

---

### Post by bdEVILord on 2009-11-04
> **cb951303 said:**
> did you try disabling desktop effects?

Yes, I have tried, no success =/

I think it's related to the graphics drivers but I don't know where to start.

---

### Post by mxc1090 on 2009-11-04
This might not be much help, but with my Maple 12 install I needed to add a couple of lines to the xmaple file before it would work:

[http://ubuntuforums.org/showthread.php?t=907702](http://ubuntuforums.org/showthread.php?t=907702)

It is referenced in post #7.

---

### Post by astrobob.tk on 2009-12-07
> **mxc1090 said:**
> This might not be much help, but with my Maple 12 install I needed to add a couple of lines to the xmaple file before it would work:

[http://ubuntuforums.org/showthread.php?t=907702](http://ubuntuforums.org/showthread.php?t=907702)

It is referenced in post #7.

I tried this (after all , the maple launcher uses the command xmaple). but still the problem persists.

"Maple is unable to render 3D graphics.
 Your operating system, graphics, or video driver may require updating.
 See 'gldriver' in the help system for more information.
 GLException
 Error making context current"

Note that  it went fine with 2D plots & that I am running Maple 13 under KUbuntu (Jaunty) in gnome.

Hope you could help.

P.S.: I am a newbie :D

thx in advance
BOB

---

### Post by schrummy on 2010-03-13
Um...i also have a problem with maple 13....i downloaded the linux version they offer.....and i can not do anything with it.... i tried sudo chmod +x to make it executable with no success.  i use archive manager and it says that the file type is not supported.....    my file name is 

Maple13Linux32Installer.bin                   did i mess up or????

---

### Post by astrobob.tk on 2010-07-20
bump

---

### Post by aschweig on 2011-12-16
I know this is a big bump, but I thought that for those similarly affected, the following might be of help:

[http://www.maplesoft.com/support/faqs/detail.aspx?sid=33530](http://www.maplesoft.com/support/faqs/detail.aspx?sid=33530)

---

