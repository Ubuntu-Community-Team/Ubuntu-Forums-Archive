---
title: "Water effect in CCSM not working"
date: 2008-11-30
forum: General Help
---

### Post by harshasrisri on 2008-11-30
even if i enable the water effect in CCSM and initiate/toggle rain/toggle viper, there seems to be nothing showing up on my desktop. I'm working with a CCSM version updated on DEC 1st on Ubuntu 8.04. How can i resolve it?

and could anyone please brief me up on how to use the widget layer, like, how to add widgets on the layer and how to toggle between desktop and Wlayer painlessly.

---

### Post by ellalan on 2008-12-01
Have you checked your Bindings setting, you can compare with mine which is attached.
EDIT: I missed that you have mentioned you have settings already done. Try click on the brush to refresh the settings to default.

---

### Post by Forlong on 2008-12-01
Not all graphics chips support water effects.
See [http://en.wikipedia.org/wiki/Pixel_shader](http://en.wikipedia.org/wiki/Pixel_shader) for reference.

---

### Post by harshasrisri on 2008-12-04
**Ellalan**
I have done as u have said but to no avail. I guess my graphics chip doesn't support the water effect as Forlong has told below. :( however, thnx a lot for the support.

---

### Post by harshasrisri on 2008-12-04
> **Forlong said:**
> Not all graphics chips support water effects.
See [http://en.wikipedia.org/wiki/Pixel_shader](http://en.wikipedia.org/wiki/Pixel_shader) for reference.
I think mine is a XMA3000 from Intel. Because DX 9.0c was the max i could run in my PC and the graphic card is Intel on-board one. If this supports water effect or not, tht i do not know.

---

### Post by unoodles on 2008-12-04
I had the exact same problem. Upgrading to Ibex fixed it. However I have noticed decreased performance with newer intel graphics drivers. I would reccommend running Intrepid from LiveCD and see if water effects work.

---

### Post by Wartender on 2008-12-04
not sure about the water, but noone has said anything about the widget layer. it depends what you want to be counted as widgets, if you use screenlets, then all you have to do is right-click the screenlet, window->widget, if you have widget layer activated, it should dissappear, and when you hit f9 (which is the default button to switch to the widget layer, it should appear.

---

### Post by harshasrisri on 2008-12-04
> **Wartender said:**
> not sure about the water, but noone has said anything about the widget layer. it depends what you want to be counted as widgets, if you use screenlets, then all you have to do is right-click the screenlet, window->widget, if you have widget layer activated, it should dissappear, and when you hit f9 (which is the default button to switch to the widget layer, it should appear.
**Wartender**
Thanks a lot! could u gimme a link or something wch says more about what screenlets are and how to add them to widget layer?

---

### Post by Wartender on 2008-12-05
you're welcome harshasrisri, here's screenlet's homepage [http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home), and i think what i mentioned above should work after you install them.

---

