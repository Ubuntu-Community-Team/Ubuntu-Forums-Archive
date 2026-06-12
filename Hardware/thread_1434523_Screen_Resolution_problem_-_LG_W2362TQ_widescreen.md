---
title: "Screen Resolution problem - LG W2362TQ widescreen"
date: 2010-03-20
forum: Hardware
---

### Post by ShayWC on 2010-03-20
Hello all.
I am new with Ubuntu and just now finished installing it on my desktop.
I have a Nvidia 5200 video card and LG W2362TQ widescreen LCD.
my problem is I cannot configure the screen resolution to be 1920x1080 which is what the screen supports.
The driver of the nVidia is installed and I used the advanced configuration to force it to work in 1920x1080. what happened is that the nVidia thinks the screen is still in 640x480 and it's like I am in a zoom-in mode.

Anyone have an idea? or even a driver for the screen? because I tried everything I could to find the driver.

Please help me.

Thanks

---

### Post by khelben1979 on 2010-03-20
Does the nVidia X Server settings tool report that your screen has been identified correctly? And what driver version have you selected?

---

### Post by ShayWC on 2010-03-20
No... The screen is CRT0 ...
The driver is nVidia version 173

---

### Post by khelben1979 on 2010-03-20
What version of Ubuntu are you running? And is the monitor connected with [dvi]("http://en.wikipedia.org/wiki/Digital_Visual_Interface") or is it using an dvi to vga converter?

---

### Post by ShayWC on 2010-03-20
I am running Ubuntu 9, downloaded just  a week ago. 
I am using a VGA cable since I am working through KVM Switch.
Ubuntu suppose to identify the screen automatically ? even Win7 couldn't do it.
Is there maybe a way to edit xorg.conf file to make it work?

---

### Post by Tikkyca on 2010-03-20
I have LG 22' monitor and ATI graphic card,after installation it detected my resolution automatically,mabie you should try changing your resolution by going to: system > preferences > display

---

### Post by ShayWC on 2010-03-21
When I go to system > preferences > display I get a message that I need to work with my nVidia driver.
Do you connect your screen via VGA? or DVI?

---

### Post by ShayWC on 2010-04-09
OK. sorry for the long time it took me to update this thread but the solution was indeed to connect a VGA cable directly without KVM switch in between. 

Thanks!

---

