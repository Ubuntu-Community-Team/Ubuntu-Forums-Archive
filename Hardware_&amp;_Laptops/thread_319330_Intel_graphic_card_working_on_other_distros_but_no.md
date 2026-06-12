---
title: "Intel graphic card working on other distros but not kubutnu"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by 1000i1 on 2006-12-15
Hi,

I have a problem with intel 945GM Express. I'm developing a QT && OpenGL application, but my grphic card is not working properly. I have to load some 3D models and they don't display as they should, so I guess that means the graphic card is not working.

I've installed this week, Fedora Core 6 and OpenSuse 10.something and in both systems my program displayed perfectly, so I'm guessing I need some drivers I don't have, but I have no idea which could it be. I have Xorg configured to work with i810 driver, I don't have resolution problems, so please don't suggest 915 resolution. 

Anyone has a clue???

The display problem is that instead of displaying all the triangles of the model, I just get some big boxes, I'll try to post an image here( maybe later if I can upload it somewhere).

Thanks for the help.

---

### Post by myturntohide on 2008-02-01
With the 945G chipset in my lenovo some applications (althogh in many instances will work in both gnome, KDE, on various distros) wont work on one to the other .

My problem was blender, I used the 820i driver with no problems at all until Blender started losing its interface in parts of the window because an item behind it in the background or on the desktop had changed like the clock changing time or the wireless animation changing.)

To solve it I used the 815 driver by selecting it manually in the screens and graphics section, it may work for you, give some feedback on ay changes.

Piddock

---

