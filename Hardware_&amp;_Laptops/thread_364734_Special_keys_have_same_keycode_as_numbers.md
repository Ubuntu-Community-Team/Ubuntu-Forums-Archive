---
title: "Special keys have same keycode as numbers"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by Curtisc on 2007-02-18
I installed Ubuntu on my tablet, and everything's working pretty well.  I got the wacom tablet to behave nicely, I wrote a little script for screen/cursor rotation, pressure sensitivity in Gimp, etc.  Now I'm trying to map the special buttons beside the screen (up, down, rotate) etc to the appropriate functions.  I followed the directions [here]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys"), but there's a problem - those special keys print numbers (1-4) in the terminal (although nowhere else).  I used Xev to determine the keycodes, and when I tried creating an Xmodmap (setting my page up button to osfPageUp, etc), not only did they not seem to do anything still, my numbers no longer worked.  I'm kind of stumbling around in the dark here - any help is appreciated, thanks.

---

### Post by akao79 on 2007-02-21
This isn't an answer so much as a question.  How did you implement the screen rotate script in gnome?   Once i get that step i'll be in the same boat as you, i noticed the same thing with regards to the buttons on my screen, they come out as numbers in the terminal.

Thanks.

---

