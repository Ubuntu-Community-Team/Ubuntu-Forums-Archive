---
title: "Will not boot, I'm retarded"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by PGrey on 2009-04-07
I just downloaded kubuntu 8.1 and everything went fine.  But when I put in my password and it goes to the next screen and reeds KDE 4.1 and shows the icons nothing happens.  I can not click on anything and the screen eventually goes permanently blank.

---

### Post by dargaud on 2009-04-07
At the login username/password screen, try to select one of the other window manager (Gnome, etc) and see if that works any better.

---

### Post by PGrey on 2009-04-07
I have tried that and it did not work.  Ive also booted with the cd and tried everythin there.

---

### Post by khelben1979 on 2009-04-07
I don't know about Ubuntu, but Debian offers the possibility to use a text based installer. This would rule out all graphical bugs which you seem to be having now.

If Ubuntu offers a text based installer, then I would suggest that you try this instead or perhaps... go for another distribution? (then you still have the possibility to go for Linux)

---

### Post by upchucky on 2009-04-07
you said that u get the login screen then it goes blank,

this indicates that it is not happy with the display and/or resolution settings in the xorg.conf file

if it does the same thing when booted with the live cd then you are gonna have to boot to a command line then edit the xorg.conf to experiment with the screen and resolution settings until  you find one that works.

search here or google your motherboard, and vid card to see if someone has traveled this path and has the right settings. could save you lots of testing.

---

### Post by khelben1979 on 2009-04-07
It would be easier to know more about how to solve your problem if you provide some information regarding your computer hardware in this thread, also.

```
sudo dmesg
``` from a text terminal gives a detalied output of your hardware.

---

### Post by PGrey on 2009-04-07
I have an Emachines M6810 piece of **** with an AMD Athlon 64 3200+ 64-Bit and a Hitachi Hard Drive 60GB, 512MB PC2700 DDR Memory. The problem occurs after I login and it goes to the window with the icons, nothing happens and then the screen dims to black. Also are you supposed to be able to click on one of the 4 icons after the login screen?

---

### Post by upchucky on 2009-04-07
pgrey,

 you really should create your own thread so to not confuse any symptoms with the original posters symptoms it helps to avoid confusion, and avoid thread hijacking which can be frustrating to the original poster as his issues can get lost in the replies.

just copy paste your post to a new thread and try to include as much info as you can.

it is better for us to post a reply to your new thread.

---

### Post by PGrey on 2009-04-07
I am the original poster, and I was trying to elaborate on my problem.  I am new to all of this though, so thank you for any pointers.

---

