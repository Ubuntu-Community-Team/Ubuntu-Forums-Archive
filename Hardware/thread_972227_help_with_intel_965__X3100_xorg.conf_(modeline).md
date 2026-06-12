---
title: "help with intel 965 / X3100 xorg.conf (modeline)?"
date: 2008-11-05
forum: Hardware
---

### Post by pwhitt on 2008-11-05
hi all...

it's a long story, but i'm trying to get my new Dell (i wish i'd never bought from them now) laptop configured.  it's a Studio 1535 w/ intel 965 / x3100 chipset & 1280x800 display.

if i use the intel driver, the machine simply gives me a useless, corrupt white screen when i run X.  if i use vesa, i get a max resolution of 800x600.

in my tinkering, i have found that this is apparently common, seemingly universal problem for this laptop/chipset combo.  i have also found that although the vesa driver limits itself to 800x600, if i use modelines to define the 1280x800 resolution, i get a screen that i can *almost* make out.  this has led me to believe that if i stumble into the right string of numbers, i might get it to work at full resolution.  (please stop me now if this is an incorrect assumption)

does anyone out there know how i'd go about getting the correct modeline?  i've tried an online modeline calculator, however i didn't know most of the info is needed to generate the modeline.  all i want is 1280x800 resolution for now.  i could care less about hardware acceleration, fancy gui enhancements and such - i just want to read a full page of text on fonts that aren't 1" tall and fuzzy.

if anyone out there can point me in the right direction, i'd be very, very happy.

i can post more info (or try to find it) if necessary to assist.

thanks!

---

