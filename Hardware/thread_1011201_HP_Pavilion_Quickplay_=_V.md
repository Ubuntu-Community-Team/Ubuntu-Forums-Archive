---
title: "HP Pavilion Quickplay = V?"
date: 2008-12-14
forum: Hardware
---

### Post by SuperD2000 on 2008-12-14
Greeting everyone. I have read a few threads on how to get the Quickplay buttons on the top of the HP pavilion laptops working, but I have an odd problem. So far all my buttons work with the exception of the actual quickplay button. I have tested to see what it does when press and currently it works just like the V key. So when I try to set it as a keyboard short cut i get an error because its the same as the v-key.

Any ideas on how I can fix this?

Thanks in advance.

---

### Post by agnes on 2009-04-19
I have the same problem.

I've tested it with **xev** but it shows exactly the same keypress/-release events as when I press (and release) the "v".
The keycodes are both 55. 

So also with some other keybindings-program you can't edit it because then you can't use the normal "v" key anymore.

By the way the rest of the HP-buttons just worked (pause, play, etc.).

Isn't there any way to assign a different keycode to this Quickplay-key?

---

### Post by agnes on 2009-04-30
*bump*

is it possible to assign different keycodes to keys AT ALL?

---

### Post by picher on 2009-05-11
i have the same problem

please any help....

---

### Post by agnes on 2009-05-26
I have read some times on the net that you should run a program called setkeycodes to assign scancodes to keycodes.
This program seems to have been installed by deafult in older Ubuntu versions.
However I can't find that program...

---

