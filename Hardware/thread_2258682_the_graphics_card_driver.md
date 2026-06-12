---
title: "the graphics card driver"
date: 2014-12-29
forum: Hardware
---

### Post by emil10 on 2014-12-29
Ubuntu Gnome (14.04.1) after installing the graphics card driver Radeon
 computer after reset freezes
after the restart nothing happens
 only black screen, computer does not respond to anything

for all your help thank you very much.
sorry as I made mistakes in writing
 I am a Pole and poorly written English,
 but I understand a lot.

---

### Post by QIII on 2014-12-29
Hello!

It would be helpful if you could tell us what model the graphics card is.

---

### Post by Mark Phelps on 2014-12-29
IF you don't know the make and model graphics card, then do the following:
1) Boot from the Ubuntu install media
2) Select the option to Try Ubuntu
3) When you FINALLY get to a working desktop, open a terminal and enter "lspci" (without the quotes)
4) Look for the line containing "VGA" -- and post those results back here

It's possible that you have a "legacy" AMD card/chipset -- whose AMD driver support was dropped last year, and forcing an install of those drivers will result in what you are seeing.

---

