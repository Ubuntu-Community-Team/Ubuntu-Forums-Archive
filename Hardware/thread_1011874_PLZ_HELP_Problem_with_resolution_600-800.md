---
title: "PLZ HELP Problem with resolution 600-800"
date: 2008-12-15
forum: Hardware
---

### Post by warzt on 2008-12-15
Now my laptop's resolution is 1280-800 but when I play game need resolution 600-800, I can't play because the screen looks like @@@@ in that game.
I think I must reinstall monitor driver but how.

---

### Post by sukhhari on 2008-12-15
> **warzt said:**
> Now my laptop's resolution is 1280-800 but when I play game need resolution 600-800, I can't play because the screen looks like @@@@ in that game.
I think I must reinstall monitor driver but how.

[PHP]
Reconfigure your Video Settings

dkpg re-configure xserver
[/PHP]

---

### Post by warzt on 2008-12-15
bash: dkpg: command not [http://ubuntuforums.org/images/editor/php.giffound](http://ubuntuforums.org/images/editor/php.giffound)
thank you sukhhari but it doesn't work

---

### Post by sukhhari on 2008-12-15
Pls use below command

sudo dpkg-reconfigure xserver-xorg

---

### Post by warzt on 2008-12-15
Thank you again, i used "sudo dpkg-reconfigure xserver-xorg" but my screen still like @@@@

---

### Post by scharkalvin on 2008-12-15
Try <ctrl><alt><-> or <ctrl><alt><+) with the - or + being on your numeric keypad (NOT the keys above your QUARTY keyboard).  Each time you do this 'vulcan salute' you cycle once through the list of possible resolutions.

To reconfigure the default resolution you need to edit
/etc/X11/x11org.conf

---

### Post by warzt on 2008-12-15
all right, now i don't play that game any more, but thank you for your help.

---

### Post by warzt on 2008-12-18
Damn now i don't play that game but i play another game and i have same problem :(
I think the point is not resolution 600-800. Perhaps I have some problem about driver. So I did try to reinstall driver but I don't know how can I get the it. I did go to linuxgraphic.org but I don't understand what it said. :(

---

### Post by dagoth_pie on 2008-12-18
what graphics card are you using?

---

### Post by warzt on 2008-12-18
This is image of my screen when I play that game: :(
[http://img376.imageshack.us/img376/8967/ca20081219001es3.jpg](http://img376.imageshack.us/img376/8967/ca20081219001es3.jpg)
I use Intel Graphic Media Accelerator 950

---

### Post by dagoth_pie on 2008-12-18
do you have compiz-fusion enabled, and is it a 3d game?

---

### Post by warzt on 2008-12-18
no, i don't run any compiz fusion when i play that game. And i think that game is a 2d game, its name is Crazy Arcade (i play korean version)

---

### Post by dagoth_pie on 2008-12-19
any other details, running it under wine or anything like that?

---

### Post by warzt on 2008-12-19
Yes, i run it under wine. And I installed directx under wine too because almost window game need directx

---

### Post by dagoth_pie on 2008-12-19
ahhh, as it just so happens i've been mucking with direct x under wine lately, found a great how to, i dont suppose you reconfigured it to use the directx dlls rather than the built in wine ones, and also, was it 9.0c you installed?

---

### Post by dagoth_pie on 2008-12-19
heres the link
[http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)
im assuming you've done all but setting it up to use the other libraries, its pretty straightforward

---

### Post by warzt on 2008-12-19
I think ubuntu run something what it make i can't play that game. Any one know the command like <clt + alt + del> like xp help i know exactly what is running under OS

---

### Post by dagoth_pie on 2008-12-19
to get that go to, system, administration, system monitor, that shows all the running proccesses.

but another way to  find out whats causing the problem is to run it in the terminal, so open the terminal (applications/accessories) then type
```
wine ./.wine/drive_c/<directory to game exe here>
```

then copy and paste what comes up, I'll read through it and see what I can see

---

