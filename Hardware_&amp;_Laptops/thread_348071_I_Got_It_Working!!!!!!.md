---
title: "I Got It Working!!!!!!"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by ctt1wbw on 2007-01-28
I got my ATI 200m and Beryl working!!!!!!!!!!!!!!  I'm getting 2500 fps in glxgears!!!!!

I'm so damned happy right now I could scream and dance the jig in the front yard naked!!!!!!!

I followed this link:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by GaryAndersonMissed on 2007-01-28
Interesting.  I just got it working and was coming to the forms to proclaim my happiness.  Nice to see that a thread was already available.  Im getting between 5000 and 5500 frames per second with glxgears.

Oh happy day. :guitar:

---

### Post by ctt1wbw on 2007-01-28
Holy crap.  With what video card?

---

### Post by roosel on 2007-01-29
I was going to post the same thing. I have an HP Pavilion ZV6000 laptop with ati 200m graphics, and over the last few days I've finally gotten graphics drivers working, and xgl/Beryl set up. I just have two issues - when I log in it seems no window manager runs, so I have to open a terminal and type "beryl-manager" and then I'm good to go (whether running xgl or standard, so this isn't a very good solution.) Second, it seems pressing shift-backspace now kills my x session, which is inconvenient when I mistype a capital letter. 
But other than that, everything works great!

---

### Post by ctt1wbw on 2007-01-29
I think I can help with one of your problems.  Go to

System
Preferences
Sessions

Then go to Startup Programs and enter:

beryl-manager

Then save it.  Now it should start when you login.

---

