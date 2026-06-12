---
title: "dual boot question (total newbie, sorry...)"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by lovecostarica on 2009-07-15
[FONT=Trebuchet MS][SIZE=3][COLOR=Navy]**Hello friends**,

This is my very first time using Ubuntu, I am extremely pleased to start learning it.

Since my own computer has been recently stolen, I have installed Ubuntu on my mother´s computer, using a dual boot in order to respect her Windows XP (*now it seems not to be the best moment to inspire my mom to learn a new system*).

The dual boot presents Ubuntu as the first option, and if one doesn´t choose anything else it begins to load Ubuntu after just a few seconds.

Considering I am still using someone else´s computer, I want it to load Windows XP by default, and only load Ubuntu if I ask.

How can I switch the order between the two systems?

Thank you immensely for your help!

**Greetings from Costa Rica!**

Daniel Thomas
[/COLOR][/SIZE][/FONT]

---

### Post by ~sHyLoCk~ on 2009-07-15
Goto Applications->Accessories->Terminal

Type:
```
sudo gedit /boot/grub/menu.lst

```
Now search for a line [should be there on top]

```
timeout   5
default   1
```

All you have to do is change it according to your need. Scroll down and see which place XP is in and put that in default.
For me it was default 4

---

### Post by lovecostarica on 2009-07-15
Yes, it worked!

Thank you immensely for your help!

---

### Post by ~sHyLoCk~ on 2009-07-15
> **lovecostarica said:**
> Yes, it worked!

Thank you immensely for your help!

Actually I have done the same things as you in my Mom's pc. Although she likes using ubuntu now. :D Sudoku ftw!

---

