---
title: "advice for partition management"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by jovianchiron on 2009-07-16
i am going to be installing jaunty, but need some help with how i should partition everything. i want to be able to do all of the desktop things i need to do, while being able to set up a file server for several other computers to access. the thing is, whatever directory many of the files are held in, i need to be able to access them from a wireless connection on a macbookpro.

in my pc, i have two harddrives, 500gb and 1tb. my questions arise in; 

1) where should i put the different paritions? 

2) what file system structures should i use? (thinking ext3), and 

3) should i install jaunty and then use gparted, or use the initial partition manager upon installation?

i have limited knowledge but am willing to learn. just remember that i'm still new to ubuntu, but have enjoyed what it has to offer so far as to not even dual boot.

---

### Post by cariboo on 2009-07-16
If you are going to install a gui, I would suggest using the desktop version instead of the server. I have 4 hard drives in my server. 
[list]
[*] /dev/sda1 20Gb ext3 / including /home mounted as /
[*] /dev/sda2  swap
[*] /dev/sda3  380Gb xfs mounted on /media/movies
[*] /dev/sdb1  400Gb xfs mounted on /media/documents
[*] /dev/sdc1  320Bg xfs mounted on /media/music
[*] /dev/sdd1  120Gb xfs mounted on /media/stuff
[/list]

I also have an external 750Gb formatted as xfs mounted on /media/external for backups.

---

### Post by jovianchiron on 2009-07-17
although your example is nice, it does little to answer my questions. could you please be more through?

---

