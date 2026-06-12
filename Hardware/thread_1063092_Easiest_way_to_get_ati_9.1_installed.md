---
title: "Easiest way to get ati 9.1 installed"
date: 2009-02-07
forum: Hardware
---

### Post by Unreal223linux on 2009-02-07
I have heard that the latest ati drivers fix the problems I'm having with my laptop.. only problem is I have no clue how to install them. I have an xpress 200m card and I need the easiest way to get the 9.1 drivers installed. 

Big thanks to anyone with some easy instructions/guides. (I have never installed anything manually before.)

---

### Post by ugm6hr on 2009-02-07
Not sure which version it installs now, but [envy-ng]("apt:envyng-gtk") is very easy.

---

### Post by mtbsoft on 2009-02-08
Simplicity itself.

Download the file (ati-driver-installer-9-1-x86.x86_64.run) to your desktop.

Now open a terminal and type...
```
cd Desktop
sudo sh ati-driver-installer-9-1-x86.x86_64.run
```

...enter your password and the installer should self extract and run automatically - then just follow the dialog instructions.

---

### Post by Unreal223linux on 2009-02-09
Thank you mtbsoft that worked great. 
This is the first time everything has worked on my laptop with any form of linux. Awesome. :D

---

### Post by Maxx730 on 2009-03-08
I installed the Drivers exactly as you said and I thought it would work but it didn't. I made a video of what exactly happens when I turn my computer on (with the new graphics card in it) even with the drivers installed. 

Watch HERE

[http://www.Maxx730Designs.com/thenew/0002.ogg](http://www.Maxx730Designs.com/thenew/0002.ogg)

---

### Post by mtbsoft on 2009-03-09
Sorry, video is restricted at work so I can't comment on that.  A few questions...

Did you follow all the instructions after the install, including the **aticonfig --initial** configuration step?
Have you tried using the recovery boot option and selecting the option to fix X?  That used to work for me when I had stuffed things up.

---

