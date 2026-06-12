---
title: "Touchpad buttons registered as two mouse devices"
date: 2014-02-15
forum: Hardware
---

### Post by razedk on 2014-02-15
I have a Lenovo R500 which has two buttons below the touchpad and 3 buttons on top of it.

All buttons works as expected, except that if using top left mouse button then I cannot drag windows using the touchpad. 

I played with xinput because I thought that it was just a question of remapping the buttons, but realized that the problem is more complicated. It turns out that the lower buttons are attached to device 12 (which is the touchpad) and the top buttons are attached to device 11 (which belongs to the famous red stick mouse). So dragging a window only works when using top left button and the red stick or lower left button and touchpad.

In Windows it is possible to use the top buttons with the touchpad, the question is, can I bind the two devices together in Ubuntu as well?

Using Ubuntu 13.10

---

