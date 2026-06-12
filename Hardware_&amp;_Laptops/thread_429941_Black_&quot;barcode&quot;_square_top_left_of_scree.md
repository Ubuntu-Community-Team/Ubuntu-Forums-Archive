---
title: "Black &quot;barcode&quot; square top left of screen"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by abovett on 2007-05-01
I've just upgraded an old PC to Feisty and am now getting a black square (looks like a bar code) in the top left corner of the screen. Rather strangely, it _usually_ disappears after I type a character into a console window or editor.

The graphics card is an ATI Rage Pro of some kind and I'm using the default "ati" driver. Changing to the vesa driver solves the problem but of course gives poor performance. I've tried changing various other settings in the xorg.conf file (resolution, colour depth, monitor refresh) without any improvement.

I have searched the forums and found these posts all of which look similar to my problem but none offer a solution (the one suggests upgrading to drivers from the ATI website but I don't see a Rage Pro driver on the ATI site):

[http://ubuntuforums.org/showthread.php?t=404682]("http://ubuntuforums.org/showthread.php?t=404682")
[http://ubuntuforums.org/showthread.php?t=408493]("http://ubuntuforums.org/showthread.php?t=408493")
[http://ubuntuforums.org/showthread.php?t=408493]("http://ubuntuforums.org/showthread.php?t=408493")

Anyone know what's causing this and how to solve it properly?

Cheers

Andy B

---

### Post by jmagsho on 2007-09-02
Andy,

I started having the same problem after a recent software update (running Feisty on an older Compaq Armada E500 with an AGP rage pro video card).   I ran xvidtune as suggested in one of the posts you mentioned and was able to correct the problem simply using the 'Auto' setting.

- Jason

---

### Post by Locutuslaser on 2007-10-03
I have two machines displaying this barcode phenomenon, a compaq E500 laptop with 7.04 xubuntu, it has a rage pro mobile. and a desktop Packard bell with ubuntu 7.04, has Rage pro card.Tried the xvidtune trick several times and selected "auto", saved it, no result. 
What else can i do?

---

### Post by dinub1 on 2007-10-03
I also had a similar problem. It showed after ugrading from 7.04 to 7.10. It showed more like some sort of garbage colors in a shape like a rectangle on the upper left. it would usually disappear. After erasing Ubuntu partitions and reinstalling from scratch (7.10 beta) issue disappeared. I assume it is some sort of graphics glitch , possibly conflicts with previous versions.

---

### Post by Locutuslaser on 2007-10-03
I installed on desktop and laptop on new partitioned and formatted hd. I assumed to upgrade to 7.10 would solve some, but if you had no result i won´t upgrade for now. The dutch forum could not help me till now/didn't show a possible solution. I think it's the ATI v cards troubeling

---

### Post by dinub1 on 2007-10-03
This "barcode" thingy showed only on my laptop. I have another copy installed on a desktop. Barcode did not show up. Incidentally the graphic card on my laptop is an ATI made card too. On the desktop is nVidia. So your assumption may be correct.

---

### Post by Locutuslaser on 2007-10-03
When i choose a low refresh rate on crt monitor on desktop, it's gone. When i choose a no-fliquerring value, eg 85Hz, it first appeared. Did the apt-get xorg## also, no result. 

I am not having problems with the barcode, but it is has not the best appearance when i want to show off ;-)

---

### Post by rpradeep on 2007-10-06
using accel off in xorg.conf solved the problem but no accellaration ugly desktop

---

### Post by Locutuslaser on 2007-10-06
The only way to solve is a reinstall and keep standard settings of video. This is answered on dutch ubuntu forum.

---

### Post by dinub1 on 2007-10-06
> **rpradeep said:**
> using accel off in xorg.conf solved the problem but no accellaration ugly desktop

I see...

---

### Post by kkratoch on 2007-12-17
I had the same trouble Dell Lattitude CPx - ATI video driver.
I was able to clear the black "bar code" by going into Applications -> settings -> screen and graphics. I selected dell 1024 x 768 laptop display with ersolution of 1024 x 768 at 60 hz and applied settings. so far the bars have not returned.

---

### Post by Locutuslaser on 2007-12-17
Thanks for reply. 

Unfortunately i have still a CRT monitor and 60Hz is too low and  flickering.

I just have done a new install with 7.10 and will report if the barcode reappear.

---

### Post by Locutuslaser on 2007-12-18
7.10 is clean now 17 inch 1024x768 @ 75Hz 

The Laptop with xubuntu still shows the barcode, will try your option kkratoch

---

