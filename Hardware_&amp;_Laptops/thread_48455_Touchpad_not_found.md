---
title: "Touchpad not found"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by sadiini on 2005-07-12
X server does not find my Synaptics touchpad and gives a fatal error. 
X org log says, that it does not find /dev/input/mice, says "no such file or directory" and terminates x session. I do have worked with this version of my xorg.conf for about 5 months now and all were fine and dandy. 
Suddenly I`m missing device called touchpad??? I have FS Amilo dual boot laptop and win can find it as usual. 
What am I possibly missing??? :-x

---

### Post by sadiini on 2005-07-12
[QUOTE=sadiini]X server does not find my Synaptics touchpad and gives a fatal error. 
X org log says, that it does not find /dev/input/mice, says "no such file or directory" and terminates x session. I do have worked with this version of my xorg.conf for about 5 months now and all were fine and dandy. 
Suddenly I`m missing device called touchpad??? I have FS Amilo dual boot laptop and win can find it as usual. 
What am I possibly missing??? :-x[/QUOTE]
 X server also says:
Cannot open device /dev/input/mice
Cannot open device /dev/psaux
Synaptic driver unable to open device
Preinit failed for input device "Synaptic Touchpad"
no core pointer
failed to initialize core devices
______________________________________________________
Yesterday I upgraded kde to 3.4.1 and shut down my little one. 
Today I opened it and got messed up X. 
Meanwhile I took a look to normal xorg.conf configurations and just in case did #sudo dpkg-reconfigure xserver-xorg and got same results as before. 
My xorg.conf looks ok, I did not drop my laptop and with windoze everything works just fine. 

Can anyone figure out, what`s wrong?
Please!?!

---

### Post by sadiini on 2005-07-13
So I`m stupid...
Well! It is a good thing, they say :) Then I have lot to learn. 
Before reinstall I tried #rmmod psmouse ; modprobe -v psmouse and "Voila!", everything started to work again :D 

Case closed. Still enyoing Ubuntu OS!

---

### Post by Zaulden on 2005-08-01
Hey. I have the same problem. My touchpad doesn't work when I boot up, but when I switch to a console, and type "rmmod psmouse" and "modprobe psmouse," it works immediately. How would I make my machine do this automatically when I boot up? Or are you still just issuing those commands every reboot?

---

