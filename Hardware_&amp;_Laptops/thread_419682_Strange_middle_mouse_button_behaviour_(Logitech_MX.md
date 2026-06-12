---
title: "Strange middle mouse button behaviour (Logitech MX1000)"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by kingfisher on 2007-04-23
Hi,

I'm using feisty since edgy was released. Since some weeks, every time I do a click with the middle mouse button (e.g. to open links in a new tab), the volume control (from kmilo) pops up. This only happens with the Logitech MX1000 mouse - if I'm using an other (ordinary corded) mouse, it works as expected. 

At the MX1000 mouse, the scroll wheel can be pushed left or right. These events seem to be mapped with volume up/down. Obviously, these events are generated when pressing the scroll wheel too (but it's not my intent).

I couldn't find any forum post or bug report about this (except that a lot of people reported, that the middle mouse button doesn't work any more at all). 

Is anyone else experiencing this problem? What can I do? I tried already different xorg.conf settings, but without any success.

Thanks,
   Christian

---

### Post by Marsan on 2007-10-30
Late reply, but i excperience the same with the middle mousebutton on gutsy now. I have mx1000 aswell. I use the middle mousebutton alot in blender and this is very annoying. Volume going up and down. I didnt realize that the middle button actually had 3 buttons. To press the wheel right down is pretty hard, so volume goes mostly up. Any fix for this issue would be great!

---

### Post by gganitis on 2007-10-30
I have a problem too with the mouse wheel. I think it has to do with the x server setup and the xorg.conf, where I was trying to install the right driver for my nvidia card, and I lost the right driver for my mouse.

I 'll search it soon. I don't know if I help you. I am a really new ubuntu user...

---

### Post by gganitis on 2007-11-05
My problem has solved. I just opened an older backup of the xorg.conf in the /etc/X11/,
copied the lines were there about the mouse, and pasted them in the running xorg.conf

---

### Post by Marsan on 2007-11-05
I also solved this problem. I used the restricted nvidia driver from nvidia.com and used nvidia-settings to create a new xorg.conf, that made the middlebuttons not to adjust the volume.

---

