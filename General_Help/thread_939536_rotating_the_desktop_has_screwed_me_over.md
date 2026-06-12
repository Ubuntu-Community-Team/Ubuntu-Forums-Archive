---
title: "rotating the desktop has screwed me over"
date: 2008-10-06
forum: General Help
---

### Post by tylerisfat on 2008-10-06
From ubuntu 8.04, hardy, i rotated the display 90 degrees. it was fine for a moment, but then when i pushed okay, the screen went black and nothing shows up. i've tried rebooting several times, and nothing is working. the only thing on screen is my cursor.

---

### Post by Blackwolf_Oz on 2008-10-06
Have you the option to boot into the recovery kernal ?
If so choose that & choose <try to fix xserver>

---

### Post by tylerisfat on 2008-10-06
so how do i rotate it once i'm there? i can figure out how to do that manually. Anyone?

---

### Post by rovae on 2008-10-06
How to use [lace wigs](http://www.royalmewigs.com)This leaflet is designed to help you put on your [full lace wig](http://www.royalmewigs.com) securely andhelp you take it off with out damaging the wig or your face!Preparing the [lace human hair wigs](http://www.royalmewigs.com/lace-human-hair-wigs-c-10.html) the underneath the wig (if there is any!) is like building foundations for a house because it will give you a solid base to pin the wigs on to. This can be done by wrapping long hair and using pin curls, crossed grips, clips or even a bandage. Covering this with a stocking top, which is also pinned on, will give you extra security.Put the wig on with help by getting the wearer to place their fingers on top of the lace whilst the assistant pulls the [fashion wigs](http://www.royalmewigs.com/fashion-wigs-c-7.html) down at the back. (Placing your fingers under the lace and pulling forward may cause the lace to tear). If on your own bend forward and pull thewig on like a hat. When adjusting it, please do not use the [lace front wigs](http://www.royalmewigs.com/lace_front_wigs.html) to pull the wig around as it may stretch or tear. Use the thick seam near the ear.

---

### Post by schmolch on 2008-10-11
screen-rotation works with intel-cards in hardy (not intrepid because of a bug in later versions of the intel-driver) and probably with nvidia-cards using nvidia's driver (not the opensource nv driver).

rotation is usually done with xrandr, like:
"xrandr -o normal" or
"xrandr -o right"

but these have to be executed in X, i dont know how to do it from console (exporting the display does not seem to work here).

---

