---
title: "OpenGL Rendering Problem"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by muraii on 2006-05-02
Hi,

I have been having an issue with my nVidia TNT2 card, specifically the OpenGL performance.  After a bit of effort (mostly learning), I managed to ensure that it used the 7174 driver, and that my xorg.conf loaded the "nvidia" driver rather than the "nv" driver.  I haven't bothered trying to push past 1024x768x24 because, well, that's fine on a 17" CRT.

After I changed to the correct "nvidia" driver, the OpenGL performance was noticeably better.  However, when I mouse over OpenGL rendered content, the rendering seems to lag, refreshing the space beneath the mouse *after* the mouse is gone.  The result is pretty ugly.

I wouldn't care if it were screensavers; but I tried to run Blender 3D--a completely OpenGL app (or nearly so)--and it's not really usable.  The menu items aren't consistently visible, the screen redraw in the wake of a mouseover is muddled, and--in general--the interface is rendered useless.

Are there any specific settings I should check into?  Is this just the state of OpenGL on Linux, for older cards?  I've read through the forums, and haven't really found anything other than advice on installing the driver.

Daniel

---

### Post by muraii on 2006-05-08
I'm using the "bump" judiciously here. I'm hoping that there is someone with sufficient knowledge to help who might not've come across it when it was fresh.

---

### Post by MP. on 2006-05-28
i have TNT2 card, and that problem in blender to.
Blender freez, then after mous over blender screen, all freez at few second, then all work fine but blender not respons, and cpu load on 100%.
It happens after rendering 75% and 100%. In other operations it happens to, but not often (it happens random).

p.s. i know english not well, sory.

---

### Post by MP. on 2006-06-01
the problem was in nvidia legasy driver. with last driver all working good.

---

### Post by tsunade on 2006-06-12
I have the same problem with OpenGL applications. When i move my mouse over something, the 'picture' underneath the mouse pointer doesn't update immidiately.
How did you fixed it?

pls help :!:

---

### Post by mindwarp on 2006-07-01
Go to the how-to forum and read about installing the most up to date nvidia driver

---

