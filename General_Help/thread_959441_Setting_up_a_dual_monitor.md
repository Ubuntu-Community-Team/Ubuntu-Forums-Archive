---
title: "Setting up a dual monitor"
date: 2008-10-26
forum: General Help
---

### Post by rmcellig on 2008-10-26
I am setting up a PC with Ubuntu on it for my Mom. I want to make it as easy as possible for her to plug in an external monitor and have it just work at the same resolution as her PC. Is this possible and how would I go about setting it up. I know that on the Mac and PC it is a no brainer all things considered.

Thanks!!

---

### Post by taqkavar on 2008-10-26
plug in the monitor, press Alt+ctrl+Backspace and re log in, should now work. You can change the resolution using System > preferences > resolution

---

### Post by Shakedown on 2008-10-26
> **taqkavar said:**
> plug in the monitor, press Alt+ctrl+Backspace and re log in, should now work. You can change the resolution using System > preferences > resolution

Chances are it won't be that easy, although the older the hardware the more support there is for it.  It's going to depend on the graphics card and graphics driver in the computer, but I would plan on spending the day with mom to get it to work.

[-o<

---

### Post by TeXtonyx on 2008-10-26
You said "dual monitor". That means having two monitors connected
to the computer at the same time which takes a special card and
then installing and configuring a driver for the card. Most people
have trouble with this so you would do well to find out the model
number of the card and "Search" for a howto at the top of Ubuntu
forum page. 

But the way you wrote about this suggested that you were going to
unplug one monitor and plug in another monitor in its place which
is much easier. If you should need to edit your xorg.conf file:

gksudo gedit /etc/X11/xorg.conf  <enter>

---

### Post by rmcellig on 2008-10-26
Sorry about the confusion. I just meant plugging in one external monitor into her laptop so that she could drag items and windows from her laptop to the larger external monitor. This should be possible in Ubuntu 8.04?

---

