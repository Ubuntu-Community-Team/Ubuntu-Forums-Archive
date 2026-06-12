---
title: "Display Issues... and slight Program Question..."
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by Antmanpro on 2007-12-18
ok heres the deal , im a pretty well versed Windows user, i know my way around well, and i can do anything i need to. But im having issues switching to Ubuntu. Here are my two biggest problems:

1. My Desktop wont display corretly, both the top and bottom bars only cover about 5/6ths of the top or bottom area they are supposed to cover, and my screen resolution is stuck on  1024x768. I have tried changeing my graphics card driver but after restarts it goes back to the default.

2. Ive isntalled Air-crack, but i can find where to open the program...

Here are my System Specs:

Gateway MT6916 Laptop
15.4inch "Ultrabright" Widescreen 
2 Gigs fo RAM
160gb HDD
Intel Pro/ Wireless a/b/g Compatable
Intel Centrino 1.5ghz Dual Core

Please help me, im very vested in switching to ubuntu, but these two issues are the biggest things keeping me from commiting to ubuntu.

---

### Post by eggdeng on 2007-12-19
You need to post your graphics card info if you want help with the first problem. To do this, copy and paste
```
lspci  | grep VGA
```
in a terminal. If you get nothing, just
```
lspci
``` & plough through the output.
```
cat /etc/X11/xorg.conf | grep Driver
```
should tell you what driver it is using.

When you install a program, you can usually run it by typing the name in a terminal. Try
air-crack
If this doesn't work, try
```
sudo updatedb
```
When it finishes updating the program database, type
```
locate air-crack
```
Try with different forms of the name like 'aircrack' until you find it. You will be able to run it by typing the complete route to the program. When you get it working, you will be able to make a shortcut.

---

