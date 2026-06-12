---
title: "Elographics"
date: 2008-04-28
forum: Hardware
---

### Post by eclipse-01 on 2008-04-28
Hello,

We want to report a problem that we see in the version of elographics that provides Ubuntu 8.04.

We have one point of sales with ubuntu as base system. In the previous
version, (Ubuntu 7.10) we don't have any problem with the driver in our POS machine (whit Elo touch screens).

We want to migrate the POS machines to Ubuntu 8.04 but the calibration is imposible (we not reach that task).

The Y axis works with the MinY and MaxY values from our previous xorg.conf (from Ubuntu 7.10) but changed (switch beetwen MinY and MaxY) but the X axis not work properly with the previuos values (and with any values). The cursor movement is inverted in the X axis, and, after loot of hours to try and error, we desist from the calibration task and, at the moment, we rest in the previous version of Ubuntu (7.10).

---

### Post by Kriss.no on 2008-07-06
I have the same problem :( Serial interface, works great in 7.10 but no go in 8.04

---

### Post by dglnz on 2010-05-30
I have just got working a serial elographics touchscreen and used this to calibrate it (file attach) you will have to compile it first then to use it 
this can be done within the GUI environment you use. 

Once it's compiled you will need to run the program from out side of the GUI enviroment (how to do this?)

at the login prompt/screen if it's not already visible click on a button (think normally there are two on the left side below the password prompt)
one of them will give you a short list one of which will be terminal prompt or console screen) **THIS IS THE ONE** once clicked you'll be faced with a blinking cursor type in you're name and next line will appear the word password type it in then you'll be dropped to the command line.

Mine look like this *[SIZE="3"]dave@main-pc:~$[/SIZE]* cd into the source directory *(I had it as /home/dave/Public/touchcal/)* so I'd type cd Public/touchcal/ once in the directory I typed sudo ./touchcal *(this then asks for my password I type it in* then the program is executed.
after each finger touch you'll be asked to press enter.
Once all three targets have been pressed you will be asked once more to press enter.

What appears next is the calibration values for the touchscreen and the resolution it is running at.

I have not tested this but if I ran the program again with the screen at 800x600 I may see a different set of values appear.

Note down the values, restart under you're GUI (if you're not comfortable with vi, vim or other commandline text editor).
As root edit the xorg.conf file and for minx, miny, maxx, maxy put in the recorded values, restart X by logging out and as before one of those buttons will have something that says reboot/restart X server, once done you should be able to see that the mouse has been calibrated for you're screen.

HTH,

Dave.





> **Kriss.no said:**
> I have the same problem :( Serial interface, works great in 7.10 but no go in 8.04

---

