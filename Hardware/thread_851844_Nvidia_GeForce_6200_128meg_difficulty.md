---
title: "Nvidia GeForce 6200 128meg difficulty"
date: 2008-07-07
forum: Hardware
---

### Post by wyattjo on 2008-07-07
the driver that came with my version of ubuntu (8.04) didn't work for my graphic card so i downloaded the nvidia version and still no luck (i got the message in the picture i attached) i can only get screen resolution of 640x480 any help would be greatly appreciated... i don't know anything about the coding of it either so i kind of need step by step stuff

---

### Post by ppc_guy on 2008-07-07
Grab Envy from Either Add/Remove or Synaptic. And you should be fine.

---

### Post by kuja on 2008-07-07
First thing I would try would be this (copy + paste into a terminal): ```
sudo apt-get install nvidia-glx-new && sudo nvidia-xconfig
```
Then log out, once logged out, press "ctrl + alt + backspace"

Failing that, maybe this: ```
sudo apt-get remove nvidia-glx-new && sudo apt-get install nvidia-glx && sudo nvidia-xconfig
```
Then log out, once logged out, press "ctr + alt + backspace"

If neither of those worked, [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by wyattjo on 2008-07-08
what do you mean by a terminal i'm a real noob lol

---

### Post by kuja on 2008-07-08
Open a terminal via Applications -> Accessories -> Terminal (Gnome) or K-menu -> System -> Konsole (KDE).  Guide: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by wyattjo on 2008-07-08
ok i got it from 640x480 to 800x600 by using the latter of the 2 codes you supplied in the terminal... is it possible to get my resolution up to 1280x1024 which is what i use in windows... i have my pc set up dual bootable

---

### Post by cocopuffz on 2008-07-08
your system might not be correctly detecting your monitor.

Open up terminal again and type "gksudo displayconfig-gtk" and try auto detect. You can try to add your monitor by manufacturer name and model type... or you can use generic/plug and play with your desired resolution in the list. For example.. in the menu it should  have something like "plug and play (1280x1024)" Apply and then restart your system. The option should be available in your disaplay menu after the reboot. 


Or not.. This works for some and not for others.

---

### Post by wyattjo on 2008-07-08
thanks guys i finally got it working i'm going to save those sudo's

---

### Post by wyattjo on 2008-07-08
i should probably open another thread for this but anyone know where i can get a canon pixma ip1600 printer driver?
also my terminal quit working and i can't resize windows and stuff and my maximize/minimize/close buttons are gone

---

### Post by starcannon on 2008-07-08
CTRL-ALT-BCKSPC will restart xserver, or just reboot, your window decorations should come back.

If your new to linux, and have been doing some modifying you will likely mess things up while your learning, don't worry most ui problems can be fixed relatively simply.

For your Printer I'd first try:
 System-->Administration-->Printing

then click on "New Printer" follow the wizard.

---

### Post by kuja on 2008-07-08
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600)

---

