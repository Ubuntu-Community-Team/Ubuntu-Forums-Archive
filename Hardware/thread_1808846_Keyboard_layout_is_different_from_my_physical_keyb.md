---
title: "Keyboard layout is different from my physical keyboard"
date: 2011-07-20
forum: Hardware
---

### Post by chejo76 on 2011-07-20
Good day to all.

Maybe someone can help me. When I installed **Ubuntu 10.04** on my pc, the distribution of my keyboard was set to Spanish (Spain) and all the keys matched perfectly. The problem started a few months ago when the sign (**@**) stopped working with the **Alt Gr** and **2** (the numbers below F1, F2, and so on).

Going to **System -> Preferences -> Keyboard** and open the Distributions tab to install a new keyboard, I can't find any one that matches the one I have. Any distribution in Spanish and their variants the **@** is next to the **Q**. If I use Alt Gr and 2 I get a **²**. Instead of the number sign (**#**) that is beside the number 4 (always below the F1, F2 ...) I get a **³**.

I tried to add a new one but in all cases, the keys do not match my keyboard. Is this a bug of ubuntu? It is very uncomfortable to be guessing where each key. The keyboard is generic and managed by evdev.

Thank in advance any help to solve this problem.

---

### Post by chejo76 on 2011-08-05
Well, never get an answer about this issue. After a long time searching for a solution, I used the xmodmap -pke command to find the keycodes of the keyboard keys.

Using the xev command, I found how the keyboard keys where mapped. With gedit, I created a file named "gedit ~/.xmodmap" with the following lines:

> keycode  10 = 1 exclam 1 exclam bar exclamdown
keycode  11 = 2 quotedbl 2 quotedbl at onehalf
keycode  12 = 3 periodcentered 3 periodcentered numbersign onethird

Typing at the terminal "xmodmap ~/.xmodmaprc" and using a text editor to verify if the new keycodes were ok. After checking that the keys were as they are in my keyboard, added the file to the starting applications (System-Preferences-Starting applications).

Problem solved now.

---

