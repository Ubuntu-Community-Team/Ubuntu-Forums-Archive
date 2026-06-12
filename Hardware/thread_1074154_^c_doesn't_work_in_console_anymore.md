---
title: "^c doesn't work in console anymore"
date: 2009-02-18
forum: Hardware
---

### Post by Clarke on 2009-02-18
Hi people plz check if you have a needed solution:

^c doesn't terminate a program in console anymore. 
stty -a shows:

intr = ^C

so it is correctly binded but doesn't work.

Any ideas?

Thanks in advance

---

### Post by andrewc6l on 2009-02-19
This will happen if for some reason your terminal is in raw mode. If so, you'll probably see a heart when you hit ^C. To fix that,
$ stty cooked

---

### Post by Clarke on 2009-02-19
Thanks for your reply but I dont see any hearts. While pushing <ctrl> the symbols of a second layout (cyrylic) are typed. 

I looked twice, <ctrl> is not binded as a layout switching key.

This situation began when I connected my new apple keyboard for the first time. Now both keyboards are connected - apple and a standard one and <ctrl>+c doesn't work on both of them, even when I disconnect my apple keyboard.

---

### Post by Clarke on 2009-06-24
Up

---

