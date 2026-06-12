---
title: "problem with rotate desktop"
date: 2008-11-22
forum: General Help
---

### Post by GameAddiction on 2008-11-22
I'm using compiz fusion on Ubuntu 8.10 and my problem is that 

1) whenever I click something on workspace, it will rotate to the right workspace. I can't even open some files on the desktop.

2) when I use scroll wheel to free rotate, it will show the image of inside the cube instead of out side the cube.

Thanks

---

### Post by eternalnewbee on 2008-11-22
Go to **Main Menu > System > Preferences > CompizCofig Settings Manager > Desktop Cube > Behaviour**, and untick Inside Cube:

---

### Post by eternalnewbee on 2008-11-22
That's for your second question. I didn't really understand your first.

---

### Post by GameAddiction on 2008-11-22
Thanks

The first question is like when I click something on the desktop even double click file on the desktop, it will rotate to right. It doesn't have to be on the edge to rotate.

I hope it will be more clear. sorry for my unclear.

---

### Post by prshah on 2008-11-22
> **GameAddiction said:**
> 
The first question is like when I click something on the desktop even double click file on the desktop, it will rotate to right. It doesn't have to be on the edge to rotate.

Check your mouse bindings for the "rotate right" settings in CompizConfig Settings Manager > Rotate Cube > Bindings.  There will be two "rotate right" there, one is for the keyboard (look for the keyboard icon) and one for the mouse (look for the mouse icon).

You can also check:
[indent]a) Rotate to cube face
b) Rotate to cube face with window[/indent] in the same tab, if everything seems fine in "Rotate Cube"

---

### Post by GameAddiction on 2008-11-22
I've done everything as you told me to but it still the same.

---

### Post by prshah on 2008-11-22
> **GameAddiction said:**
> I've done everything as you told me to but it still the same.

Disable the "Rotate Cube" plugin. Does left clicking work fine now? If it does, then it is a mouse bindings setting problem.

If it is still a problem, disable the "Desktop Wall" plugin, and check again.

---

### Post by GameAddiction on 2008-11-22
Although I disable every action that use mouse, it still the same if I don't disable rotate cube or desktop wall.

When I disable rotate cube and desktop wall, it works fine.

---

### Post by prshah on 2008-11-22
> **GameAddiction said:**
> 
When I disable rotate cube and desktop wall, it works fine.

Which means that it is most likely a mouse binding in "Desktop Wall".

---

