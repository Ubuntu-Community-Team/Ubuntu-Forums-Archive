---
title: "Trident CyberXP4 Not working..."
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by PooingCavy on 2007-01-17
The Trident CyberXP4 is like messing up my computer! while attempting to run the live CD, it displayed really, really weird colors, it had some lines, most of them red, all vertical, and some strange grey fading effect, and other stuff. the ubuntu live CD worked for the "Start/install ubuntu, start in safe graphics mode, check disk for defects, check memory, boot up from first HDD", but in both start modes it did t he safe, although the phenomenon was the same, it was slightly differed (safe mode had some different lines). Can anyone tell me whats going on. I have a link:

[http://www.hidesafe.com/cgiproxy/nph-proxy.pl/010110A/http/youtube.com/watch?v=ADhc4VWkGFE](http://www.hidesafe.com/cgiproxy/nph-proxy.pl/010110A/http/youtube.com/watch?v=ADhc4VWkGFE)

---

### Post by Sqwishy on 2007-01-22
This is the proper link [http://youtube.com/watch?v=ADhc4VWkGFE](http://youtube.com/watch?v=ADhc4VWkGFE) ... the above one doesn't work.
My friend has a similar problem, he's trying to install edgy on a 'toshiba satellite pro 4600'
It seems like it errors with GDM, so probobly some weird drivers. try pressing ctrl + alt + f6 to get a text only terminal, see if it works.

P.S. Don't trust Mr Clean! :wink:

---

### Post by PooingCavy on 2007-02-03
bump.

when do i do the ctrl alt f6 thing tho

---

### Post by PooingCavy on 2007-02-03
btw, im gonna try feisty fawn

---

### Post by PooingCavy on 2007-02-03
I Need Help I Need Help I Need Help I Need Help I Need Help!

---

### Post by tehdon on 2007-02-11
I have a Toshiba m1. It uses the same graphics card. The cyberbladexp4-(prolly)32m.  This card can either use the trident driver, or the vesa driver.  I have been lucky enough to not have any problems with either Dapper or Edgy, as far as initial bootup and install graphics being corrupted.  What I would try is using the alternative install disc, which I believe has a text only install option.  Then I'd edit the xorg.conf file and change the driver from trident to vesa and see if that works for ya.  You might also try adding the "cybershadow" "true" to the xorg.conf file.  As a last ditch you might get a knoppix live cd and boot with the fb1024x768 magic option.  

BTW, there does not appear to be any active development for the trident driver.  There is no 3d accel, but there is basic 2d accel.  You can watch a full screen DVD or a couple of divx all at once, but running anything 3d is painful!

---

### Post by matthewboh on 2007-03-06
Just in case you are watching this post, I found the answer to my Tecra M1 video issues here [http://www.ubuntuforums.org/showthread.php?p=2256732#post2256732]("http://www.ubuntuforums.org/showthread.php?p=2256732#post2256732")

---

### Post by PooingCavy on 2007-05-27
YAY! Thx... My dad wont let me mess with the video drivers though... any safe installation?

---

