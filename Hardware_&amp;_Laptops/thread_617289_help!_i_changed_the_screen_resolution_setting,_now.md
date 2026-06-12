---
title: "help! i changed the screen resolution setting, now i can't see anything!!!!"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by exica on 2007-11-19
help! i changed the screen resolution setting, now i can't see anything!!!!

i was connecting my laptop to a monitor and changed the resolution setting for the laptop screen somehow. now everything on my screen is distorted and i can't see anything to change it back.....



i have tried using the external monitor ( still i cant see anything)....


does anyone know how to change the resolution settings without looking at the screen? ( the sequence of keys to press maybe) 

can someone please help me if they know, because i was planning to take my laptop away with me on teh 28th for  a 7 month trip around south east asia. and now i can't use it...

-thanks!

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-19
Hi, what desktop you are using? Is it gnome (Ubuntu) or kde (Kubuntu) ?

I don't know how to do this in KDE, but this works in gnome (Ubuntu):

[LIST=1]
[*]Press **Ctrl+Alt+F1**
[*]Login from there (using your username)
[*]Type this:
```

pico /home/**yourname**/.gconf/desktop/gnome/screen/default/0/%gconf.xml

```
*Change **yourname** with your login name.*
[*]In line number 6, you will find your current resolution, change the value inside <stringvalue>**change-this-one-only**</stringvalue> with a known working resolution.
[*]Press **Ctrl+O** to save
[*]Press **Ctrl+Alt+F7** to back to X, and press **Ctrl+Alt+Backspace**, but I must note you, if there's any unsaved document, you will loose it.
[/LIST]

---

### Post by exica on 2007-11-21
hi thanks for the reply! 

i'm using Ubuntu 7.10.

when i type in:

pico /home/yourname/.gconf/desktop/gnome/screen/default/0/%gconf.xml

the lines don't come up, instead i get wha tis shown in the attached photo...

what should i do from there? am i doing anything wrong???


sorry, i don't understand how it works : /


thanks for your help

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
Have you change the "yourname" to your login name?

Type this to get your login name:
```
whoami
```

Replace "yourname" in the path previously with the output from that command.

If the "whoami" output: "exica", you should change the path into:
```
pico /home/**exica**/.gconf/desktop/gnome/screen/default/0/%gconf.xml
```

---

### Post by drmatty on 2007-11-23
I'm having the same problem. I tried returning the resolution in gconf to the original resolution of my screen, and it's still not working. The "image" that shows on the monitor is distorted, as pictured above, and not filling the laptop screen. Any recs?

---

### Post by drmatty on 2007-11-23
So I solved my problem and have my new monitor working.

Cntrl+alt+F1

sudo dpkg-reconfigure xserver-xorg

answered questions and reset my video driver

plugged in monitor and reset resolution to monitor's resolution. Had all of my problems when I was trying to setup multiple monitors, etc. I no longer want to use the native monitor for my laptop, so this fix works for me. Hope this helps.

---

