---
title: "Mouse doesn't move while typing"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by LordFiodor on 2007-02-04
Hi there,
i'm having a big problem here, because i've edited some preferences which makes that my mouse doesn't move while typing, but i can't remember where i did that. Actually, it is quite impossible to play FPS games. the funny thing is when is plug off the mouse (I'm having an acer travelmate notebook) i can move the mouse free while typing. i've already tried to use another user or change the desktop environment (I'm using Gnome), but it doesn't work properly either. so actually it has to be a global xserver setting or so. please help, i'm getting mad with that problem :(

---

### Post by xjgnsdof on 2007-11-19
I have the same problem, and I'm trying to play Far Cry in Cedega.

---

### Post by xjgnsdof on 2007-11-19
I just found out the solution.

Edit the file "/etc/default/mouseemu" and put 0 in place of 300 in the line ```
"TYPING_BLOCK="-typing-block 300""
```

Make sure to uncomment that line by removing the # symbol. Finally, restart mouseemu by inputting ```
sudo /etc/init.d/mouseemu restart
``` into Terminal.

Enjoy!

---

