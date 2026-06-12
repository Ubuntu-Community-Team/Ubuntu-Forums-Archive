---
title: "Microsoft vx-1000 webcam"
date: 2009-07-02
forum: Hardware
---

### Post by TheMixtureMedia on 2009-07-02
Hi there I am tring to get my vx-1000 webcam working in kubuntu 9.10 and all I have is a blank screen does anyone at all know how to get this fixed??

---

### Post by jesterthejedi on 2009-09-13
I have this cam. It took me a long time, 6 months to get the right driver up and working. Here is what I recommend:

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file - located on the left bar
extract and change directory
in terminal type "make" no quotes, takes a few mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

UPDATE! if you have errors on the MAKE step, you can use "make distclean" "make clean" then "make menuconfig" and deselect the other drivers included, I had errors trying this on my upgrade to karmic alpha 4 & 5. After the last step run a normal "make" and "sudo make install"

---

### Post by osos on 2009-11-02
Hi!

I'm also running kubuntu 9.10 and have the same problem.
I tried the solution you provided, but I get make errors even with the make clean, make distclean etc.
I also tried the solution of mr. Stanca from this [http://ubuntuforums.org/showthread.php?t=885795&highlight=microsoft+vx-1000&page=11](http://ubuntuforums.org/showthread.php?t=885795&highlight=microsoft+vx-1000&page=11) thread to no avail.
Any and all help would be appreciated.

---

### Post by SuperMau on 2009-11-04
Got mine working!!! :D

I haven't tried the [http://linuxtv.org/hg/~jfrancois/gspca/]("http://linuxtv.org/hg/%7Ejfrancois/gspca/") drivers, I used [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2) and they worked fine. 

The only problem was the same as the others are having, make problems with the firedtv-1394 driver before compiling sonixj driver which is the one we really need. So, after make failure, you have to edit v4l/.config (you have to run make first or else you won't find .config in the v4l directory):

CONFIG_DVB_FIREDTV=m

to

CONFIG_DVB_FIREDTV=n

Run make again and then sudo make install, reboot, enjoy!

Cheers
SuperMau
Ubuntu 9.10 with kernel 2.6.31.14-generic

P.S. (You could also do make menuconfig ad disable the firedtv-1394 driver)

---

### Post by jesterthejedi on 2010-01-19
> **SuperMau said:**
> Got mine working!!! :D

I haven't tried the [http://linuxtv.org/hg/~jfrancois/gspca/]("http://linuxtv.org/hg/%7Ejfrancois/gspca/") drivers, I used [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2) and they worked fine. 

The only problem was the same as the others are having, make problems with the firedtv-1394 driver before compiling sonixj driver which is the one we really need. So, after make failure, you have to edit v4l/.config (you have to run make first or else you won't find .config in the v4l directory):

CONFIG_DVB_FIREDTV=m

to

CONFIG_DVB_FIREDTV=n

Run make again and then sudo make install, reboot, enjoy!

Cheers
SuperMau
Ubuntu 9.10 with kernel 2.6.31.14-generic

P.S. (You could also do make menuconfig ad disable the firedtv-1394 driver)

This no longer works with the new Kernel 2.6.31.17.

---

