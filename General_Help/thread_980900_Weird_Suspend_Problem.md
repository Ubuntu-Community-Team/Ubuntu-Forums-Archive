---
title: "Weird Suspend Problem"
date: 2008-11-13
forum: General Help
---

### Post by zaomaster on 2008-11-13
I've got an old Latitude C600 that works wonderfully except that it cannot resume from suspend/hibernation properly.

When I turn the machine back on, things go well for a second and then the screen wiggs out, draws things very weird, and is very slow at responding.

However, if I can get to a terminal (CTRL+ALT+F1) and restart gdm (sudo /etc/init.d/gdm restart), everything works perfectly.

Anybody have any idea what to do?

---

### Post by tvtech on 2008-11-13
start looking at your debug log,  it sounds like your not reintializing X properly.  it's probably not sending the right signal to your video card.   


are you using a proprietary video card driver?  or a standard vesa driver? 

if your using proprietary, try.... reinstalling the driver, try using the vesa driver instead, try using a different version of the driver.

---

### Post by zaomaster on 2008-11-13
Thank you so much! I was using the opensource radeon driver, but by switching to the vesa driver it now works perfectly!

---

