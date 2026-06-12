---
title: "Ati 200M Driver"
date: 2010-03-19
forum: Hardware
---

### Post by Donut417 on 2010-03-19
I was hopeing to find the driver for a ATI 200m?

The machine:

HP Pavillion 5222nr
160Gig hard disk
1 gig of ddr ram
ATI 200M with up to 128 megs of memory shared. 
Ubuntu 9.10 - the Karmic Koala

other info: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00737397&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3231992](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00737397&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3231992)

They link above is to the product specs page from HP. Further more, are the Linux drivers from ATI as good or better than the windows ones? The reason I ask is because I have had crappy drivers from them before, if they are crappy, is it even worth installing them? 

I appreciate any help. :p

---

### Post by I8NY on 2010-03-20
the driver should be easy to install by going to System>Administration>Hardware Drivers and it should search and then show a ati driver to install.  There are other ways to do it if this doesn't work but this is the easiest.

---

### Post by Donut417 on 2010-03-20
Doesnt come up under there. I do have the catylist control center installed and it cant find a compatle graphics card.

---

### Post by I8NY on 2010-03-20
well if you have to control center and it doesn't detected it then i would just give up on getting the driver working.  You will only lose 3D support but it should be okay for 2D stuff.  On board graphics are not that good but if you want 3D you might want to try ati open source driver but it doesn't work with ever chip.

---

### Post by Donut417 on 2010-03-21
[http://www2.ati.com/drivers/linux/linux_8.16.20.html](http://www2.ati.com/drivers/linux/linux_8.16.20.html)

I found that and according to this my card is suppost to be compatble. But maybe I could try the open source driver, its probley better than ATI's crapy programed one any way.

I tried Envyng and it didnt work.

---

### Post by Donut417 on 2010-03-21
I just rememeber that I forgot to tell you that this is the 64bit version Im using. I think thats the problem. I know windows is very particluar about having 64bit drivers and I dont think ATI makes a 64bit driver for this card. So I think im screwed.

---

### Post by jocko on 2010-03-21
> **Donut417 said:**
> I just rememeber that I forgot to tell you that this is the 64bit version Im using. I think thats the problem. I know windows is very particluar about having 64bit drivers and I dont think ATI makes a 64bit driver for this card. So I think im screwed.ATI no longer supports your card and the last proprietary driver to support it  (catalyst 9.3 = fglrx 8.593) does not work in any ubuntu release newer than 8.10. So the open source driver is your only hope.
And 64 bit has nothing to do with it (ati has released 64 bit versions of their drivers for years, and all of the catalyst releases are combined 32 and 64 bit installers).

---

### Post by ublintu on 2010-03-21
Yes, the open source is the only one and nothing in hardware drivers. 
You can't play 3D games, but you can have compiz.
Good luck.

---

