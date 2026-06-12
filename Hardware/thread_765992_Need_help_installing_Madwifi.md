---
title: "Need help installing Madwifi"
date: 2008-04-24
forum: Hardware
---

### Post by griehl2490 on 2008-04-24
I just installed Hardy on my laptop. I'm a first time linux user and I want to learn how to work it and I like the way it works so far.

I have an atheros wireless card and I'm pretty sure that I need the madwifi driver but I'm not really sure has to how to go about installing it. I have the tar.gz file downloaded but I have no idea where to go from here.

Thanks for the help.

---

### Post by fhantazm on 2008-04-25
Which laptop and which wifi card? Many, including myself, have had problems using madwifi with Atheros based cards. The method using ndiswrapper wrks great on atheros 5007.

---

### Post by griehl2490 on 2008-04-25
> **fhantazm said:**
> Which laptop and which wifi card? Many, including myself, have had problems using madwifi with Atheros based cards. The method using ndiswrapper wrks great on atheros 5007.

Compaq Presario F700 Laptop
Atheros AR5007 802.11 b/g Wifi Adapter

Edit: Looking at your Sig, it looks like we have the same laptop specs. I have a AMD Turion64x2 at 1.9 GHz, 2 GB of RAM, 160 GB HDD, nVidia 7000m and the Atheros 5007.

---

### Post by dstew on 2008-04-25
Did you install 32-bit or 64-bit Hardy?

---

### Post by griehl2490 on 2008-04-25
The 64 bit one. I clicked the mark to get the AMD 64 CD or whatever it is.

Oh and is there a way that I can see my files that I have on my windows partition in my ubuntu part. (I have ubuntu installed inside of windows). I don't want to have to have duplicates of all 5300 songs to play in ubuntu too.

---

### Post by fhantazm on 2008-04-25
If you would have installed the 32bit, I could walk you through the steps I took to get mine working. However, many people have had issues getting Atheros drivers and 64bit Ubuntu to play nice together. If you decide to install the 32bit version PM me and ill help you along.

EDIT: As far as being able to use windows partitions in Ubuntu, it mounted my NTFS partition right after install. It even put a nice icon on my desk for me. I'd say part of your problems are 64bit driver related. Unless you are dead-set on 64bit, I would suggest going the 32bit route. Youre only running 2gb RAM so for you, theres no major benefit to going 64bit.

---

### Post by griehl2490 on 2008-04-25
> **fhantazm said:**
> If you would have installed the 32bit, I could walk you through the steps I took to get mine working. However, many people have had issues getting Atheros drivers and 64bit Ubuntu to play nice together. If you decide to install the 32bit version PM me and ill help you along.

EDIT: As far as being able to use windows partitions in Ubuntu, it mounted my NTFS partition right after install. It even put a nice icon on my desk for me. I'd say part of your problems are 64bit driver related. Unless you are dead-set on 64bit, I would suggest going the 32bit route. Youre only running 2gb RAM right so for you, theres no major benefit to going 64bit.

Should I go back and install the 32 bit? I don't really know the difference between them. I'm not computer illiterate or anything. Thats just one of the things I never really understood. But yea. I can go back and install the 32 bit one if necessary.

---

### Post by fhantazm on 2008-04-25
I would suggest it. But again, thats just my opinion. I have had very little trouble getting it(32bit Hardy) to run on the F700 series. Everything is installed except for the wifi, which is easy enough to do with ndiswrapper.

---

### Post by griehl2490 on 2008-04-25
> **fhantazm said:**
> I would suggest it. But again, thats just my opinion. I have had very little trouble getting it(32bit Hardy) to run on the F700 series. Everything is installed except for the wifi, which is easy enough to do with ndiswrapper.

I'm installing the 32-bit version as I type. So what exactly do I do then to get it working with ndiswrapper once the time comes?

---

### Post by fhantazm on 2008-04-25
Cool deal. This is what I did and it worked like a charm. 

I also PMed you with my yahoo id if you need more help. 

[http://ubuntuforums.org/showthread.php?t=749481](http://ubuntuforums.org/showthread.php?t=749481)

---

### Post by griehl2490 on 2008-04-26
Thanks a lot. Running the 32-bit version now with no problems. Still can't see my windows files but that wasn't my immediate problem that I wanted to solve. I have my graphics card back up and running along with ndiswrapper for my wireless card and it is running smoothly. Thanks for the help :)

---

### Post by fhantazm on 2008-04-26
Sure! No problem! Glad you got it working!

Im not quite sure why youre not able to see your windows files, but Im sure others have had that problem and there are posts about it. I will also look to see what I can find for you.

---

