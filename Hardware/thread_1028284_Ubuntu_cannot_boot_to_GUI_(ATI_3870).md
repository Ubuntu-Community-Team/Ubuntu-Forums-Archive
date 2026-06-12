---
title: "Ubuntu cannot boot to GUI (ATI 3870)"
date: 2009-01-02
forum: Hardware
---

### Post by powerplayground on 2009-01-02
I have an ATI 3870 Video Card, and I can only access the text based command line. Whenever it try to load the GUI the screen just turns black. I am completely lost and I don't know where to start. 

Also to the Ubuntu team: WTF! Why does Ubuntu lack native support for ATI cards?

---

### Post by powerplayground on 2009-01-02
Bump!

So yeah no luck in ubuntu, kubuntu or fedora. I canoot get any type of GUI to load, how do I config my gfx setings in text mode. HELLLLLPPPPPPP

---

### Post by nick09 on 2009-01-02
Did you have a different graphics card installed on your machine before? If so you need to put the old graphics card in and disable the last drivers or disable compiz.

---

### Post by powerplayground on 2009-01-02
This is a fresh install. Heres what I did to try to "fix" this POS:
-Tried to edit xorg.conf (empty)
-tried to generate a new xorg.conf (Temp file running, deleted now it cant est. any listening sockets.)
-No commands regarding Xorg work ever, what the hell do I do?
Heres a question... Why does a gui need to be a server?

-I got around to disabling Xorg and gdm but whenever I try to I start back at sqaure 1: A black screen. All google results have proven unsuccessful >.<

---

### Post by markbuntu on 2009-01-02
You need to boot into recovery mode from the grub screen. Then you can use the xfix option which will set the VESA driver. Then you need to get all the updates and reboot again before you can use the restricted driver.

If you upgraded from Hardy 8.04 it is very important that you remove all the old fglrx drivers and kernel modules before you enable the new restricted driver or future kernel updates will fail.

---

### Post by powerplayground on 2009-01-03
I finally managed to fix this problem.

My xorg.conf file was blank, so thats what was confusing me >.<

Here's a guide how to fix this problem
1.Press Ctrl+F2
2.Login and type in "cd etc/X11"
3.type this in: "sudo nano xorg.conf", put in your password.
4.In the editor add this line (If your file is empty): Driver "Vesa"
5.Cress Ctrl+X, then hit "y".
6.Restart, you will boot to a prompt that will ask to change the configuration of your driver. You will want it to generate a new configuration file.
7.Restart again and go back into text-mode (Press Ctrl+F2)
8.type: "sudo nano xorg.conf", put in your password again
9.Under the "Display" line type, or replace the existing Driver line to: Driver "Vesa"
10.Cress Ctrl+X, then hit "y".
11.Restart and hopefully you will be greeted by the GUI :D

---

### Post by Beaon on 2009-04-25
I'm experiencing the EXACT same behavior with an upgrade from 8.10 to 9.04. I have a Radeon 3870x2 I'm not sure if there is some pattern going on here.

Any how 8.10 worked just fine so I don't know why it's all fubard now. I am going to try powerplaygrounds suggestion and will post here if it works.

---

### Post by Beaon on 2009-04-25
This is terrible guys. 8 hours ago I had a happy working Linux machine now the GUI is toast. :(

I've tried Xfix or whatever.
I tried powerPlayground's suggestion. My Xorg.conf was not empty and adding that line did nothing.

When Ubuntu loads normally the new loading bar shows up but then the screen goes literally nuts flashes several times and eventually it just bumps into a crazy screen thats checkard and such. I can boot into my Xp 64bit just fine and before I upgraded  I could boot into 8.10 just fine.

This is terrible, what happened? How can I get backup and running? :(

---

