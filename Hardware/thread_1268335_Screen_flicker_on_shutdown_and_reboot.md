---
title: "Screen flicker on shutdown and reboot"
date: 2009-09-16
forum: Hardware
---

### Post by larynx on 2009-09-16
I have Ubuntu 9.04 32-bit running on a Toshiba Satellite M305-S4910. Recently I disabled the bootup splash screen from grub and ever since whenever I shutdown, reboot, and sometimes when I go into a console (by pressing CTRL+ALT+F1) the entire screen flickers and at the top of the screen there is cropped text also flickering. I would like to keep my grub configuration as it is but this is really annoying, is there anyway to solve it?

---

### Post by dbuell on 2009-09-17
I'm having a similar issue, but I did not disable a bootup splash screen for grub. I am running Ubuntu server 9.04_64. When I boot with the option vga={any vga mode here} the screen flickering is on only the grub screen, but if I boot without that option the screen flicker exists on all of my tty's. 

My motherboard is a d945gclf2 and it has no flicker problems on the POST splash screen or POST information screen.

When it is flickering in grub and tty the monitor reports:

70hz@720x400

however when I use the screen on another computer running Ubuntu Desktop it reports

60Hz@1600x1050
(The correct and maximum resolution for the monitor)

---

### Post by larynx on 2009-09-17
I have noticed that if I go into the console (CTRL+ATL+F1) it flickers as usual but if then I go back into GDM (CTRL+ALT+F7) and then shutdown/restart it won't flicker.

---

### Post by mo0nykit on 2009-10-04
I also have the same problem.

I'm running Ubuntu 9.04 on an Acer Aspire 4520 (Nvidia 7000m, proprietary drivers 180.x). My screen goes black at the center with white around the edges, and a LOT of flickering. This happens when I switch consoles (Ctrl-Alt-<function key>) and also during the shutdown process (I can't see the shutdown splash).

I hope someone can help out. Thanks!

---

### Post by mo0nykit on 2009-10-05
Guys I found a solution over at **#ubuntu**. I wrote it here:
[http://ubuntuforums.org/showthread.php?t=1282338](http://ubuntuforums.org/showthread.php?t=1282338)

---

### Post by Baljamin on 2009-10-05
I have a Laptop model "dell d610" with *flickering screen*. i dont know the the solution i think there so many champs who can bring me out for this situation.........

---

### Post by mo0nykit on 2009-10-05
Does the screen flicker while in the GUI? It probably has something to do with refresh rate. I don't know how to go about your problem, but at least I'll give you a possible lead.

---

### Post by burcaden on 2009-10-14
baljamin, first you unistall your graphics driver and update ur windows graphics driver after reboot i hope so i will never happen again ohterwise you should check ur vga (graphics card )

---

### Post by moorking on 2009-10-30
i am using windows xp Since the install my screen has been constantly flickering. I tried all the usual suspects. I updated the video card driver, and even went to the nvidia website to get the lates 64x vista compatible driver. I lowered my screen resolution, and refresh rate. Nothing worked.

---

### Post by larynx on 2009-12-10
I updated to 9.10 and the flickering stopped.

---

