---
title: "Installation/graphics problem"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by jon_elwood on 2006-02-07
Just installed ubuntu as a dual boot on my laptop with xp.  I have an HP dv8025ea with AMD64 Turion.  It froze on installation but typing "install apci = off" worked fine.

Now that it is installed and boots up it gets as far as the gui, the screen goes weird with several ghost images and flashing bars, information about "xserver" appears the it reverts to a command line input.  how do  get to the gui?  what is this xserver about?

J

---

### Post by joey111 on 2006-02-07
ctrl+alt+ F1 (or f2,f3,f4,f5,f6) ->commandline Gui, back with ctrl+alt+F7

---

### Post by m4rqz on 2006-02-07
The xserver is the driver for you graphics card, and it is brobably that driver that is broken somehow. I'm not sure that I can help, but what would help others to help you is some information about your system: what graphics card (ati or nvidia) are you using? what architecture (what processor, that is; intel p4 or amd xp for example) are you running on? you could also post the contents of /etx/X11/xorg.conf (a text file that contains the configuration of the graphical system). If you can't do this last thing, you can try to write "cat /etc/X11/xorg.conf | grep Driver" into the command line input and hit <enter> and post whatever appears after it. 
Cheers

---

### Post by jon_elwood on 2006-02-07
its an ATI Radeon Express 200M (128)

1.8 AMD Turion 64 Processor.

I'm told ubuntu doesnt like ATI - how do i configure linux to work with it/configure xserver?

---

