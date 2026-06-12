---
title: "cpu heat"
date: 2008-05-08
forum: Hardware
---

### Post by pixelized on 2008-05-08
hello,

i recently added an extra hd for my ubuntu pc,and a new graphics card(nvidia 256mb fx5500),would these addtional components affect my cpu,especially the heat,and what is the supposed normal/average temp for a cpu? should i replace my cooling fans..i was wondering about because at start up,im hearing some weird sound coming from one of the fans, and it goes away after a while..i installed the heat sensor from the add/remove program and the average that i got was system:45c,cpu:45c ,hd0: 56c, hd1:58c temp1:40c

thanks!

---

### Post by Rocket2DMn on 2008-05-08
Temperatures vary from system to system, depending on your hardware like the processor, chassis airflow, etc.  Since you are replacing the video card and HD, you probably don't need to add/change anything else.  Newer video cards might run a little hotter, but any case with moderate airflow should take care of it.
56C & 58C seems a little hot for a hard drive, though.

When you change out your video card, you may need to reconfigure X if the login screen doesn't appear.  You can do that by booting into the recovery mode console and running
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Then you can tweak your graphics settings with new drivers from within Ubuntu.  You may need to uninstall restricted drivers before the upgrade, too.

---

### Post by dreadlord_chris on 2008-05-08
Your hard drives seem to be running a little hot - just as an example, and remember systems will vary, my 2 hard drives tend to fluctuate between 25c & 40c (38c & 27c atm)

---

### Post by pixelized on 2008-05-09
> **Rocket2DMn said:**
> Temperatures vary from system to system, depending on your hardware like the processor, chassis airflow, etc.  Since you are replacing the video card and HD, you probably don't need to add/change anything else.  Newer video cards might run a little hotter, but any case with moderate airflow should take care of it.
56C & 58C seems a little hot for a hard drive, though.

When you change out your video card, you may need to reconfigure X if the login screen doesn't appear.  You can do that by booting into the recovery mode console and running
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Then you can tweak your graphics settings with new drivers from within Ubuntu.  You may need to uninstall restricted drivers before the upgrade, too.


thanks..as you have suggested i guess i was having problems with the airflow,and also the close proximity of my 2 hd's so i adjust  its spaces and opened up my cpu case by removing some covers..

---

