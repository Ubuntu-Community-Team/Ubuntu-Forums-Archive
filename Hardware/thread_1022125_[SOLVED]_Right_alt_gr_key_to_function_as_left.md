---
title: "[SOLVED] Right alt gr key to function as left"
date: 2008-12-26
forum: Hardware
---

### Post by azr on 2008-12-26
My right alt key currently functions as a meta key. I would like to change it to behave as the left alt key does. 

I have used xev to determine the keycode of the right alt to be 108. Though not knowing quite what to set it to (using xmodmap) have tried a few things but no success. 

I have also tried changing keyboard layouts to UK and US ones (instead of the current ZA (South Africa) one i use)

Any advice?

---

### Post by azr on 2009-01-04
I found solution [over here]("http://blog.andrewbeacock.com/2007/06/getting-right-alt-key-alt-gr-to-work-in.html").

The solution is selecting the **Alt and Meta are on the Alt Keys** option under the keyboard preferences. 

In Ubuntu this option is found under: System -> Preferences -> Keyboard.

In Kubuntu 8.10 (ibex):
Applications -> System -> System Settings -> Regional & Language -> Keyboard Layout -> Advanced (tab) -> Alt/Win Key Behaviour.

---

