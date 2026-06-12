---
title: "Extended desktop problem 9.04 dell laptop"
date: 2009-04-25
forum: Hardware
---

### Post by gizmo2007 on 2009-04-25
Hello.  I am having issues getting the extended desktop to work on my dell latitude D500.  Please help.

It has the Intel 855GM. 

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
video                  25360  0 
output                 11008  1 video

My xorg.conf is stock.

When I activate the external monitor and uncheck mirror monitors it asks me to set virtual resolution then it extends the desktop.  The problem is after logout and login, my desktop is extended, but it is literally stretched across both screens, the menu bar is stretched, the "applications" button is 6" long.  The strange thing is that the image of the bar is all stretched out, but where you click is still in place.

I have always had a problem with the extended desktop.  I can't find anywhere to tell it which screen is the primary screen.  It always tries to put the menu bars on the external screen and the icons on the laptop screen.  But the "Stretched" problem is new.

What I need is this.  Extended desktop, the laptop as my primary screen with all the icons and menu bars, and the external monitor open, ready for presentation on a projector.

Can anyone help me get this working properly?  Is there a better driver I can use, or a better conf tool, or can I write my own xorg.conf to get these results. Thanks for your help.

---

