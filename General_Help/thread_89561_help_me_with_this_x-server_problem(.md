---
title: "help me with this x-server problem:("
date: 2005-11-12
forum: General Help
---

### Post by corey? on 2005-11-12
ok i just wrote this before and it got erased when i pressed the wrong key so im going to be quick about this sry...:mad: 

anyway, i cannot see the login screen when i boot into linux and its said that i have an x-server problem. its said that it cannot detect any devices, symbols, or screens. i went to the dpkg-reconfigure xserver-xorg command . most of the stuff in there drew a blank in my mind of what i should put ... so i did my best and still x-server error. i want to know if i have to save the changes somehow or how to correctly configure it...:confused: (system specs below)

hp a730n
x800xl vidcard
p4 hyperthreading 3 ghz
partioned 200gb sata hd(for linux and windoze)


btw, yes i am i big linux noob:( 

and help will be very appreciated, thanks!

---

### Post by Qrk on 2005-11-12
In the first screens of the dpkg-reconfigure xserver-xorg command, you'll be asked to select a driver. There are a ton to choose from, but not all work. Depending on your monitor, you should choose the appropriate one. If you don't know which one to use, google your monitor. You can get to a graphical environment using the "vesa" one, which should work with most hardware.

---

### Post by corey? on 2005-11-12
[QUOTE=Qrk]In the first screens of the dpkg-reconfigure xserver-xorg command, you'll be asked to select a driver. There are a ton to choose from, but not all work. Depending on your monitor, you should choose the appropriate one. If you don't know which one to use, google your monitor. You can get to a graphical environment using the "vesa" one, which should work with msot hardware.[/QUOTE]


ok ill try

---

### Post by corey? on 2005-11-12
thanks changing the thing to vesa did the trick...:eek: 


thank you!!!!!!!!!!!!!!!!!!!!!!!11

---

