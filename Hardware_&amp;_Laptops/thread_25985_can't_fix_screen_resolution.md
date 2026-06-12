---
title: "can't fix screen resolution"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by scorpion on 2005-04-11
I  installed Hoary last week and the first problem was with the resolution. I tried dpkg-reconfigure xserver-xorg and xorgconfig but they don't work. The only resolution avalaible is 640x480. I can't post my xorg.conf file right now as i'm in WinXp but i read somewhere else that the first resolution in "Modes" will be the default. it started at 1280x1024 and went down from there. i've also tried to change my verty and horisync, doesn't work either. thanks in advance. monitor is Dell E772c and i have an Integrated Graphics chipset 845G

---

### Post by alastair on 2005-04-11
Post your Xorg.conf and the X logs :

/var/log/Xorg.0.log

---

### Post by scorpion on 2005-04-11
Here's the xorg.conf file. The var/log/Xorg.0 log file is 30 pages and unable to upload.

---

### Post by scorpion on 2005-04-11
Now X server and the gdm cannot start, and the keyboard is unresposive right at that point.  Very frustating, i think i'll go shoot something now.  :-x  Perhaps there's a way to install xfree86 and remove Xorg? I'm a newb, forgive me.  :-?

---

### Post by alastair on 2005-04-11
The log file is important. If it is too long, perhaps you can trim some of it? There is sometimes a lot of obvious repetition/uninteresting parts. 

Otherwise, compress and upload.

---

### Post by scorpion on 2005-04-11
Here's the log. Have fun! keyboard has decided to be good now.

---

### Post by scorpion on 2005-04-12
It's not worth this much frustration, I tried a bunch of live cd's over the weekend which had Xorg instead of Xfree86 and they all had problems with the monitor. Maybe I'll come back to it at a later time. Thanks for your replies.

---

### Post by alastair on 2005-04-12
Well I hope you check back anyway, because I have a suggestion.

FIRST - if you modify the conf file - take a BACKUP i.e.

cd /etc/X11
sudo cp -p xorg.conf xorg.conf.orig

Log out - be at the GDM/login screen and switch to a different VT (e.g. CTRL+ALT+F1). Log in here.

In the log :

DRI is disabled "because it runs only at depths 16 and 24". I would try :

DefaultDepth	24

in the "Screen" section of the xorg.conf file.

Then, restart GDM :

sudo /etc/init/d/gdm restart

Looking better?

If not - back to VT1 (CTRL+ALT+F1) and try :

DefaultDepth	16

Then, restart GDM :

sudo /etc/init/d/gdm restart

Any help?

---

### Post by scorpion on 2005-04-13
I tried xorgconfig again just for the hell of it, and it finally got it right. Thnks for your replies.  :smile:

---

### Post by heimo on 2005-04-20
Scorpion: Could you share your xorg.conf and/or hints how to get 845G to cooperate with Dell monitor - I've tried to help Someone on  [this thread]("http://www.ubuntuforums.org/showthread.php?p=140814")  but unfortunately without luck.

---

### Post by heimo on 2005-04-20
double post, ignore - MODS feel free to delete this post

---

