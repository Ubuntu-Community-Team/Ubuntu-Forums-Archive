---
title: "Samsung Galaxy Book Pro Sound"
date: 2021-10-08
forum: Hardware
---

### Post by gonemusic on 2021-10-08
Dear forum members,

could anyone help me with my speaker/sound problem? Simply I cannot hear anything on my Samsung Galaxy Book Pro 13" running ubuntu 21.10.
I tried updating to the latest stable kernel and also tried manually updating [https://github.com/thesofproject/sof-bin](https://github.com/thesofproject/sof-bin).

There is also this post: 
[https://forum.manjaro.org/t/howto-set-up-the-audio-card-in-samsung-galaxy-book/37090](https://forum.manjaro.org/t/howto-set-up-the-audio-card-in-samsung-galaxy-book/37090)

Unfortunately there is no 
/etc/modprobe.d/sof.conf 

so I am not sure where I should continue.


Thanks in advance!

---

### Post by T6&amp;sfpER35% on 2021-10-08
[https://bbs.archlinux.org/viewtopic.php?id=269385](https://bbs.archlinux.org/viewtopic.php?id=269385)

---

### Post by gonemusic on 2021-10-09
Thank you, but this post does not really help. It is the same information as in the manjaro post. I already did what I could as described in my first post. What am I missing?

---

### Post by T6&amp;sfpER35% on 2021-10-09
yes sorry ,after i posted the link i saw it leads to same link you posted
and unfortunately there's no delete/undo post option

---

### Post by gonemusic on 2021-10-10
No worries, thanks for trying.

---

### Post by gonemusic on 2021-10-10
I installed Manjaro LInux now. Speakers work with the above tutorial.

---

### Post by gonemusic on 2021-10-11
Unfortunately in Manjaro I have random Kernel Freezes. :(

Edit: For anyone interested...updating to the latest stable kernel seemed to fix it.

Edit2: Nope, still happening. Will try 21.10 again.

---

### Post by gonemusic on 2021-10-19
I got it working now. If anyone else needs help just ask.

---

### Post by QIII on 2021-10-19
Please post your solution so that it is available to others without asking.  Don't make others who might benefit from your solution come looking for you.

---

### Post by gonemusic on 2021-10-19
Will do when I have the time. To put it simply I followed the manjaro "how to" from above but the difficulty was in fixing the errors I got :)

---

### Post by gonemusic on 2021-10-19
[FONT=arial]**_Problem 1: firmware-sof-signed not in repository_**

1. Get it directly from git hub: git clone [https://github.com/thesofproject/sof-bin](https://github.com/thesofproject/sof-bin) 

[U][B]Problem 2: firmware-sof-signed install script not working 
[/B][/U][/FONT][FONT=arial]1. Use the instructions below (dont forget to move the old files first)

cd v1.9.x
rsync -a sof*v1.9   /lib/firmware/intel/
ln -s sof-v1.9      /lib/firmware/intel/sof
ln -s sof-tplg-v1.9 /lib/firmware/intel/sof-tplg
rsync tools-v1.9/*  /usr/local/bin

[U][B]Problem 3:  /etc/modprobe.d/sof.conf & /etc/modprobe.d/blacklist.conf do not exist


[/B][/U]Don´t worry, simply create both files.

[/FONT]
[FONT=arial][U][B]Problem 4:  Blacklist snd-hda-intel

[/B][/U]The tutorial simply says to add "snd-hda-intel". It is in fact "blacklist snd-hda-intel"


[FONT=arial][U][B]Problem 5:  stupid mistake

[/B][/U]Read carefully and replace your username where YOURUSERNAME stands ;)

Hope some finds this helpful.

Kind Regards


[/FONT][/FONT]

---

