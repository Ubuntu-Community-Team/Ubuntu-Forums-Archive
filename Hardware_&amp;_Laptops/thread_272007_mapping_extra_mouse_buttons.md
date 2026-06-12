---
title: "mapping extra mouse buttons"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2006-10-05
Hi all. I have a Toshiba Satellite 4300, and it has the two extra mouse buttons between the space bar and the main curved ones.

Is there a way to make these switch desktops, like Ctrl-Alt-Left/Right? (that's in gnome.)

Thanks.

---

### Post by tlwolf on 2006-10-06
I would start by going to the termanl and running xev figure out if its a keyboard or a mouse button. If its a keyboard look into xmodmap and xmacro. If its a mouse I would look into imwheel. If you have any questions post em but I wont be back till sunday.

---TLWolf---

---

### Post by xmastree on 2006-10-07
**xev**? hmm... Very useful. 8) 

Right, according to that, they're mouse buttons 4 and 5, which explains why they currently behave like a scrollwheel.

**imwheel** it is then. I'll try that and hopefully have a solution when you get back.

---

