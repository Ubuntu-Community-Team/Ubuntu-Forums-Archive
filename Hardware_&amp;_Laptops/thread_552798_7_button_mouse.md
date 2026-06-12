---
title: "7 button mouse"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by ward83 on 2007-09-16
I am trying to get my new mouse to work, it is a Ideazon Reaper 7-button mouse. It has 3 thumb buttons on the left side, which I want to use to control compiz fusion. I am trying to get them to initiate the shift switcher, scale, and expo plugins. However, after several hours of trying different configurations, I am unable to get it to work. The extra three buttons on the mouse function as Home, End, and Backspace keys, respectively. I have verified this using xev, which shows KeyPress events instead of button events. Any ideas?

---

### Post by ward83 on 2007-09-17
Anyone? I'm wondering if this could be a hardware or driver thing, and I may just return this mouse for another one.

---

### Post by uzerzero on 2007-09-17
Using "xmodmap" should allow you to map those keys to some other function. I don't know what the keycode for Home, End, and Backspace are, but using xev should show what it is. Then you can have xmodmap remap the buttons to another unused button, and after that have Compiz-Fusion use it as shortcuts.

---

