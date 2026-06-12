---
title: "How to install adobe flashplayer in firefox."
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by baltadt on 2009-09-14
I had the same problem and here is how I fixed it....

1) copy this tutorial to tomboy notes

2) download the tar.gz file to your desktop (save file not open) at..

[http://get.adobe.com/flashplayer/tha...Linux_(.tar.gz]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.tar.gz"))

3) extract it to your desktop

4) close firefox (very important)

5) open a terminal window (applications-accessories-terminal) and enter the following


sudo cp /home/USERNAME/Desktop/libflashplayer.so /usr/lib/firefox/plugins

enter password

(make sure you replace your username for USERNAME. make sure Desktop is typed with a capital D.

6) open firefox click Tools----add-ons----plugins. this should have installed the new plugin called shockwave flash 10.0 r32

Have fun on hulu.com, smallworlds.com and other sites

---

### Post by w00ly on 2009-09-14
I just installed flashplugin-nonfree via synaptic and it did the same stuff you did :)

---

### Post by baltadt on 2009-09-14
I tried that and about a dozen others things from other threads and could not get it to work.  That is why I posted this, for the others out there that have the same results as me.

---

