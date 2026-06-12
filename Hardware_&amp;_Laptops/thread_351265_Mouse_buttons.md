---
title: "Mouse buttons"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by acorn22 on 2007-02-01
I have a usb wireless Logitech mouse of some sort that has wheel tilting buttons.

I would like use these are back/forward buttons. How do I go about doing this?

---

### Post by daou on 2007-02-01
I'm assuming you mean back and forward in firefox.

Find out what button numbers the tilts are mapped to with "xev". If not already installed, sudo apt-get install xev

Let's say xev reported your tilt buttons as "button 4" and "button 5". Then you add something like this to your ~/.Xmodmap file:

pointer = 1 2 3 6 7 4 5 8 9 10 11 12 13 14 15 16 17 18 19 20

See 6, 7 and 4, 5 have switched places. FF interprets button 6 & 7 as back and forward so we need to put them wherever 4 and 5 where. Now the tilts are interpreted as button 6 & 7. Or you can switch the order of 6 & 7 if the functions are backwards (if tilt right goes back).

After rebooting/restarting X it should work.

---

