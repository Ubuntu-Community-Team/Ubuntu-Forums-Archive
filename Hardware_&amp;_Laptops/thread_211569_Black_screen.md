---
title: "Black screen?"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by mech7 on 2006-07-08
I have installed ubuntu and i get a black screen when botting.. i can boot from the dvd in vga safe mode though.. from the live dvd. But how can i get it working now? I don't know anything from linux :p

I have an Acer Travelmate 4100 i'm pretty sure it has an ati x700 mobile card in it.

---

### Post by Okami on 2006-07-08
I should probably not answer because I am a beginner myself. I had the same problem the first time I installed Ubuntu... What I did back then was not correct but at least I could get through the black screen.
I booted in recovery mode from grub menu and at the command line write sudo nano /etc/X11/xorg.conf and find the "Section Device" and change the driver from ati to vesa, then ctrl o to save and ctrl x to exit then sudo reboot.

But perhaps you should wait for an answer from someone more skilled :)

---

### Post by shakumafu on 2006-07-08
note: i am a beginner too

okami's  solution is right, but it should be more of a temporary fix as using the generic(vesa) driver will not have 3d support(if you want 3d support). the black screen could be that ubuntu didnt properly configure the xorg.conf file so it is stuck with an error behind the splashscreen. you may be able to get to the terminal(command line, w/e) from the black screen by pressing ctrl+alt+f1

---

### Post by mech7 on 2006-07-08
When i do "sudo nano /etc/X11/xorg.conf " in the command line i get some sort of dos editor with a black screen? :shock:

---

### Post by Okami on 2006-07-08
You get a text file which you have to edit. Its like a dos editor but its a linux editor... I think ^_^ Find the "Section Device" in the file and change the drivers.

---

### Post by mech7 on 2006-07-08
yeah but all i get is black there is no text ?

---

### Post by Okami on 2006-07-08
Check if you wrote wrong or something :confused: maybe you did and it open a new file with nothing in it. If so close that file without saving.

---

### Post by mech7 on 2006-07-08
it does say new file but i typ exaclty this: sudo nano /etc/X11/xorg.conf

---

### Post by Okami on 2006-07-08
Then I do not understand, I am sorry :confused: It is sudo nano /etc/X11/xorg.conf 
If it says it is a new file, then I can only think you are writing it wrong...:( I am sorry.

---

### Post by mech7 on 2006-07-08
mm it might be the capital X.. gonna try again :p

---

### Post by mech7 on 2006-07-08
woei i got it working thanks.. it was the capital i found on another forum this was a common problem as it tries to set it to other display device or something..

this works adding to device:

option "MonitorLayout" "LVDS,AUTO"

Supposedly this is allready an old bug for all mobility ATI cards.. wonder why it doesnt add this with installation then :confused:

---

### Post by mech7 on 2006-07-08
damn when i now go to the console the screen gets all weird and shakey and with lines :o

---

### Post by mech7 on 2006-07-08
strange now its normal again.. video driver must be buggy :confused:

---

### Post by sylverwing on 2006-07-08
I have an Acer Aspire 1694 also with a X700 and I installed the fglrx driver[LIST=1]
[*]Install the *xorg-driver-fglrx* package from the Restricted repository

*sudo apt-get install xorg-driver-flgrx*

*sudo apt get install linux-restricted-modules-$(uname -r)*
[*]You now need to configure the computer to use the new driver so run this command in a terminal:

*sudo dpkg-reconfigure xserver-xorg*
[*]When the dialogue appears and asks whether to do automatic detection of your video, pick Yes.
[*]When asked to select a driver, pick fglrx.
[*]Follow the remaining instructions as appropriate.
[*]Restart your machine for changes to take effect.[/LIST]

With the option "MonitorLayout" "LVDS,AUTO" i got rare transitions of white magma. So if can't get it right then try this. 
Good luck. Newbies helping each other. ;)

---

### Post by mech7 on 2006-07-10
mmm i tried it then it says ths?

chris@chris:~$ sudo apt-get install xorg-driver-flgrx
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@chris:~$

---

