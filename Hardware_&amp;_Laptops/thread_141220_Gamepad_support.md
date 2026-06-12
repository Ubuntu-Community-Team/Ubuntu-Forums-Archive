---
title: "Gamepad support?"
date: 2006-03-07
forum: Hardware &amp; Laptops
---

### Post by goatflyer on 2006-03-07
I have a ProPad 6 gamepad which I use often to play ZSNES on the Windows side of my dual boot machine.  I have also installed the ZSNES version from the repository on my Ubuntu side, but that ZSNES says no joystick was detected.

I can't seem to find the Ubuntu equivalent of something like Control Panel where I can select and set up my gameport adapter for Ubuntu...  what am I doing wrong / missing ?

---

### Post by Kegir on 2006-03-08
I'm a noob so I can only partialy help.  ( I think I found directions on here but not sure so sory for not giving cred) This is for USB devices only.  How do you Install the old school gamepad ports?  Anyone?

First install joystick
open terminal
sudo apt-get install joystick

then tell it to start at boot (not sure how to do this part, can someone fill me in)  I currently have to reconfig at each boot.

next 

sudo apt-get install jscalibrator
tell apt-get yes if it asks for something

Then plug in your pad and put the following in the termianl
sudo chmod 666 /dev/input/js0

in terminal type jscalibrator to config

for additional pads 
sudo chmod 666 /dev/input/js1
and use jscalibrator to config

---

