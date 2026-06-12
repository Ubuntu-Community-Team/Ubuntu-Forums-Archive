---
title: "xrandr rotates diplay but doesn't rescale screen"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by freund on 2007-10-27
After upgrading to Gusty on my lenovo X60 tablet the screen doesn't rescale with a rotation. In other words a screen with a 1024x768 that is normal when rotated by xrandr -o left  should be 768x1024 with everything rotated, but what happens is the display rotates but stays 1024x768. I other words if I force a window to go full screen it goes off the end of the dislay because it is real 768x1024. it worked fine in fiesty.

Can anyone help me on this?

---

### Post by vmsda on 2007-11-13
On my X41 Tablet (with newly installed Gutsy) the rotation and resizing work ok, after I configured the swiveling acpi events, according to instructions in ThinkWiki forum for IBM laptops.

I have another problem regarding **xrandr:** I can rotate the screen any way I like with **xrandr -o 0|1|2|3**, but when I try to query with **xrandr -q**, it does not tell me what the current screen orientation is, just all possible orientations! Does anybody know how to solve this?

---

### Post by freund on 2007-11-14
> **vmsda said:**
> On my X41 Tablet (with newly installed Gutsy) the rotation and resizing work ok, after I configured the swiveling acpi events, according to instructions in ThinkWiki forum for IBM laptops.

I have another problem regarding **xrandr:** I can rotate the screen any way I like with **xrandr -o 0|1|2|3**, but when I try to query with **xrandr -q**, it does not tell me what the current screen orientation is, just all possible orientations! Does anybody know how to solve this?
mine works I get  

$ xrandr -q
Screen 0: minimum 640 x 480, current 768 x 1024, maximum 1024 x 768
default connected 768x1024+0+0 right (normal left inverted right) 0mm x 0mm
   1024x768       60.0*
   800x600        60.0
   640x480        60.0

note I am rotated right with 768x1024 but my maximum is stuck at 1024x768 Is there a way of rotating the maximum?

---

### Post by vmsda on 2007-11-15
> **freund said:**
> mine works I get  

$ xrandr -q
Screen 0: minimum 640 x 480, current 768 x 1024, maximum 1024 x 768
default connected 768x1024+0+0 right (normal left inverted right) 0mm x 0mm
   1024x768       60.0*
   800x600        60.0
   640x480        60.0

note I am rotated right with 768x1024 but my maximum is stuck at 1024x768 Is there a way of rotating the maximum?

You are rotated right, as you say, yet your xrandr -q command still yields "... (normal left inverted right) ...". That was just my point, it is not showing the current orientation, otherwise it would yield " ... right ... " only. Which Ubuntu are you running?

---

### Post by freund on 2007-11-15
I am running Gusty

---

### Post by vmsda on 2007-11-15
> **freund said:**
> I am running Gusty

Yes, so am I ... wonder if this problem is somehow related only to Gutsy and not to other Ubuntus ...

---

### Post by freund on 2007-11-16
> **vmsda said:**
> Yes, so am I ... wonder if this problem is somehow related only to Gutsy and not to other Ubuntus ...

Actually it was an upgrade from Fiesty and I had difficulties with direct rendering of on the display so I had to uninstall xorg and reinstall it. I figure that I might have to do a complete  clean install because there is some config file somewhere messing things up.

---

### Post by vmsda on 2007-11-16
> **freund said:**
> Actually it was an upgrade from Fiesty and I had difficulties with direct rendering of on the display so I had to uninstall xorg and reinstall it. I figure that I might have to do a complete  clean install because there is some config file somewhere messing things up.

Maybe you can save yourself the trouble; I did a clean install and we have exactly the same problem.

---

### Post by Mormiriel on 2007-11-16
*sighs* I'm having the same problem. I had a wench of a time re-tweaking my old script to work, and even now, it rotates, but doesn't go into portrait. I have no idea how to solve this, so I guess we'll all just sit around waiting for someone smarter to figure it out. LOL

---

### Post by freund on 2007-11-16
> **Mormiriel said:**
> *sighs* I'm having the same problem. I had a wench of a time re-tweaking my old script to work, and even now, it rotates, but doesn't go into portrait. I have no idea how to solve this, so I guess we'll all just sit around waiting for someone smarter to figure it out. LOL

The bizarre part is in Fiesty it worked.

Was yours a fresh install? or an upgrade? I hate to do a fresh install since the configuration time to set it takes a lot of time.

---

### Post by Mormiriel on 2007-11-16
I just upgraded.
And I agree, it is bizarre. I hate when things that worked before suddenly stop when you "upgrade".
:mad:

---

### Post by vmsda on 2007-11-17
> **freund said:**
> The bizarre part is in Fiesty it worked.

Was yours a fresh install? or an upgrade? I hate to do a fresh install since the configuration time to set it takes a lot of time.

We have two problems here: freund and mormirel have problems with the rotation and/or resolution; I have problems with the incorrect response to the xrandr -q command.

If it worked in Feisty, then we are in trouble and in real need of a specialist to tell us how to achieve compatibility between xrandr and the new kernel. Does anyone know how we can report possible bugs to the Ubuntu organization?

---

### Post by freund on 2007-11-17
> **vmsda said:**
> We have two problems here: freund and mormirel have problems with the rotation and/or resolution; I have problems with the incorrect response to the xrandr -q command.

If it worked in Feisty, then we are in trouble and in real need of a specialist to tell us how to achieve compatibility between xrandr and the new kernel. Does anyone know how we can report possible bugs to the Ubuntu organization?

You can check to see if the bug was reported at [http://www.ubuntu.com/search/node/bug+report](http://www.ubuntu.com/search/node/bug+report)
If not you could try to report it.

It would be nice to know if someone with a X60 tablet actually got the xrandr working.

---

### Post by gubemton on 2007-11-23
Fix for Kubuntu:

[https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/121342](https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/121342)

It's a problem in libqt3-mt. You need to grab the libqt3-mt source and apply the patch listed in the bug report. Hopefully it should work after that.

---

### Post by vmsda on 2007-11-24
> **gubemton said:**
> Fix for Kubuntu:

[https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/121342](https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/121342)

It's a problem in libqt3-mt ...

What about us, gutsy children? :(

---

### Post by Mormiriel on 2007-11-26
> **gubemton said:**
> Fix for Kubuntu:

[https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/121342](https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/121342)

It's a problem in libqt3-mt. You need to grab the libqt3-mt source and apply the patch listed in the bug report. Hopefully it should work after that.


I'm afraid I must play the part of the ignorant here:
I have a libqt3-mt update according to my adept package manager, but I still have the issue. I couldn't interpret the comments on the bug report link you posted, so perhaps that's my missing piece.
Can someone explain, please?

---

### Post by freund on 2007-11-26
I believe its a deeper problem than with KDE. I use Windowmaker as a window manager and it doesn't use KDE components and it still suffers fro the same problem. Its either in Xorg or xrandr or messed configuration due to upgrade.

---

### Post by freund on 2007-11-30
I solved the prob|em, at least for myse|f. It was an issue with the video driver.
With the upgrade xorg.conf stuck with the old driver "i810". When I switched to the "intel" driver it worked. Now I can rotate left or right with proper scaling.

---

