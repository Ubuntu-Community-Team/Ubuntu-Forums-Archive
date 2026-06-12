---
title: "Screen spanning with Dell Latitude D830 HELP!!"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by mblind on 2007-11-29
I have a Dell Latitude D830 with a NVidia Quadro NVS 140M video card and I am trying to span from my notebook screen (Primary Display) to a NEC Multisync 1530V LCD Monitor. (Secondary Display)

The Screen and Graphics settings (Under System/Admin) are clear enough on how to do this but this look kind of crazy when the 2nd Monitor is hooked up.. The best way to describe it is it looks like I have zoomed in alot on my display.. I have to scroll around to see everything... Not good.

Any EASY way of fixing this..  I have read about Twinview etc. etc. but that is beyond my safety net with an OS. I don't want to screw up all this work I have in Ubuntu..  This is really simple stuff in Windoze and on a Mac.. There has to be an easy way in Ubuntu.. Right?

Any advice? Thanks in advance.!!

---

### Post by mblind on 2007-11-30
I fixed my own problem..
Just typed (In Terminal)

gksudo nvidia-settings


If you have an Nvidia card with newish drivers this will bring up a nice little GUI and bam.. Super easy config after that.

---

