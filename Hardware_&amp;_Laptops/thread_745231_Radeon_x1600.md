---
title: "Radeon x1600"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by doubad on 2008-04-04
Alright, so I'm sure this is something that keeps coming up but i recently got Ubuntu (Gutsy) and tried installing the non-free Ati drivers for my Radeon 
x1600.  Surprise surpise I can only get to the load screen and once the drivers are applied, I'm left with a black screen.
Has this problem been solved? does anyone know of a thread where they actualy solve it or of an alternative that doesn't leave me in 2d.  I really want to keep Ubuntu and I had perfect 3d in Fedora so I'm not sure what should be done.

---

### Post by doubad on 2008-04-04
anyone?

---

### Post by mcnikolas on 2008-04-04
go to /etc/X11/xorg.conf .I think that this is the problem.I do not think that you can solve it now.Reinstall Ubuntu and make a copy of the file, so if you have any problems with your drivers you will replace the old xorg.conf.

---

### Post by msjones on 2008-04-04
What are you wanting to do with X1600? Compiz etc??

This worked for me.... Fresh install of Gutsy (Though for ati I highly recommend the new 8.04 beta release) enable the restricted drivers reboot do a full system update reboot again and all should be working fine.

Let me know how you get on.

---

### Post by bookgekgom on 2008-04-04
Ok so...You have x1600. Go to ATI site download ur driver and install it. And sudo gedit /etc/X11/xorg.conf and change ur driver to "fglrx" Now save and restart your pc. it must be fixed NOW :D

---

### Post by Saint Angeles on 2008-04-04
it took me forever to setup my ATI with gutsy... hardy was totally easy.

im using the newest fglrx from the ati site. i'm attatching a copy of my xorg.conf...

---

### Post by doubad on 2008-04-05
Excellent, thank you guys for all your responces.  Unfortionately I'm away from the computer until tommorow.  I will update you as soon as i can.

---

### Post by Bannor on 2008-04-05
Hey Ati actually did a pretty good job of making driver support for linux and doing so in such a way that your average joe can get it working. 

1.  if you don't need 3d don't bother,  no matter what every system related thing I do in linux takes me a few hours.
2 link to ati site [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html). find your card download the driver. make the program executable  (not sure but I thing the best bet is to use the sudo command in terminal followed by a path to the downloaded executable) 
3.you may get a few errors.  I actually thought it didn't work until I rebooted and right there in my applications was the ATI control center. 

I will attach a scene shot of the ati program.  I apologize if this is too vague a discription of what needs to be done I am a sales guy when something doesn't work right I just try every google How-to untill the problem is fixed or I break the os and have to start from scratch

---

### Post by doubad on 2008-04-06
yess, I had this exact catalyst program last week when I had Fedora.  That installed quite simply.

---

### Post by doubad on 2008-04-07
Alright, so none of that worked for me BUT I decided to download Hardy instead.  It was mentioned above that it was much easier to install on Hardy, any advice on doing this?

---

### Post by Wobedraggled on 2008-04-07
> **doubad said:**
> Alright, so none of that worked for me BUT I decided to download Hardy instead.  It was mentioned above that it was much easier to install on Hardy, any advice on doing this?

Grab EnvyNG and do it that way.

---

### Post by Flynn555 on 2008-04-09
hmmm...whenever i dl the linux driver for my card  my system wants to open it with wine...am i doing something wrong?

---

### Post by Yellow Pasque on 2008-04-09
AGP or PCI-e? If it's AGP, don't hold your breath waiting for driver support from ATI...

---

### Post by Flynn555 on 2008-04-10
I GOT IT!!!

i just followed the "method 2" manual installation from this page [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

it worked just follow them exactly.

---

