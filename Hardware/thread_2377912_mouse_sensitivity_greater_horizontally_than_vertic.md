---
title: "mouse sensitivity greater horizontally than vertically"
date: 2017-11-17
forum: Hardware
---

### Post by JohnDillinger43 on 2017-11-17
Just finished installing 16.04 64-bit on an old system that previously had 12.04 32-bit.  Under 12.04 the mouse worked normally (Logitech M705), but since the upgrade the sensitivity seems to be twice as much horizontally as vertically, rendering it difficult to use.  I'm guessing it's because I'm using dual monitors, but this wasn't an issue before.  I just spent the last hour reading about synaptics and conf files and horiz/vert scrolling options, but I know very little when it comes to anything regarding hardware interaction, and I'm at a loss of how to fix this issue (or apparently even describe it, unless I'm literally the only person who's ever run into this).

---

### Post by efflandt on 2017-11-18
I have used various Logitech mice, most recently an Anywhere MX until its M1 button started acting up from gaming (now cleaned with contact cleaner and working for laptop duty), and currently MX Master. I have never noticed a difference between horizontal and vertical scrolling with those or other Logitech mice. However, I did notice 16.04 being much more sensitive than previous Ubuntu versions because it uses default mouse acceleration of 5 instead of previous 2. That works fine for a mousepad, but not so good for a regular mouse. So I specifically change sensitivity of my mouse without changing sensitivity if I use a mousepad on a wireless keyboard.

In a terminal window do **xinput** to see what the id of your mouse is below **Virtual core pointer**. Then see if the following reduces sensitivity where **id#** is the id number of the mouse in xinput:```
xinput --set-ptr-feedback id# 5 2 1
```That sets the mouse to move 5 pixels in a short period of time before it accelerates, then accelerates 2 pixels at a time (instead of default 5 pixels at a time). If that does what you want, go to the "Search your computer" icon at the top of the Unity bar, type **start**, open "Startup Applications", then Add a startup application with the xinput setting that you want, so it will run that setting every time X starts.

---

### Post by JohnDillinger43 on 2017-12-05
Awesome -- that worked!  I guess with the increased acceleration I just noticed it more horizontally since I have two monitors and so have more horizontal space than vertical.

---

