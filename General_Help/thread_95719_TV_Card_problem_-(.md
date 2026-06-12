---
title: "TV Card problem :-("
date: 2005-11-27
forum: General Help
---

### Post by Kika556 on 2005-11-27
I'm new to linux, i have Ubuntu 5.10 installed and it works perfectly! :p 
I still have some problems with my TV Card.

I found it like this in gallery:
[IMG]http://www.bttv-gallery.de/photo0065.jpeg_easy_tv_a.jpg[/IMG]
It has PAL BG Tuner, looks like this one (100%), remote control is also the same.
I am using TVtime, i tryed Zapping also but same thing, no picture, signal, sound, even on composite... :(
What should I do?
Thanks in advance!
P.S. 
Sorry for my English! :)

---

### Post by Irtimid2001 on 2005-11-27
i also have the same problem, i have a hercules "smart tv" card, and it's not working in Ubuntu. Goodluck with it, i've tried many methods and everything failed until now.

---

### Post by Kika556 on 2005-11-27
Hope that somebody can help us...;) :)

---

### Post by Kika556 on 2005-11-28
Anybody?!?:(

---

### Post by patrickfromspain on 2005-11-28
in zapping try using capture mode instead of overlay. I have an Avertv go and it only in capture mode.

---

### Post by Kika556 on 2005-11-28
Thank's for your reply!
Tryed but same thing... :( 
I can't even reach overlay mode, it says Error. :( 
Every help is apreaciated!

---

### Post by teprrr on 2005-11-28
Hercules Smart Tv Stereo has something wrong and it cannot be identified automatically. Thus you've to specify the card number to the bttv module. The correct number is 100, though I haven't been able to get any sound out of my card after changing from Debian to Kubuntu...

---

### Post by Kika556 on 2005-11-28
[QUOTE=teprrr]Hercules Smart Tv Stereo has something wrong and it cannot be identified automatically. Thus you've to specify the card number to the bttv module. The correct number is 100, though I haven't been able to get any sound out of my card after changing from Debian to Kubuntu...[/QUOTE]
Do you know correct number for my card?:???:

---

### Post by madjo on 2005-11-28
You might want to take a look at this post:
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)
most notably the link in the post, which will get you to a list of Linux supported tuners.

it helped me. :)

---

### Post by Kika556 on 2005-11-28
THANK YOU!
It works perfectly now!
Thank you once again, this could also help to others!
I found my Card No. 62, with tuner No. 1, but i don't get any sound.
I will fix that, i hope!:p 
Thank's to everybody! ;)

---

### Post by Irtimid2001 on 2005-11-30
still not working for me, it's still all fuzzy (gray-black-white). Can anyone tell me which tuner a "hercules smart tv" card has, i haven't found it so i took tuner=4 (no tuner)

---

### Post by teprrr on 2005-11-30
[QUOTE=Irtimid2001]still not working for me, it's still all fuzzy (gray-black-white). Can anyone tell me which tuner a "hercules smart tv" card has, i haven't found it so i took tuner=4 (no tuner)[/QUOTE]
No idea, but if that card is same as smart tv stereo, try card=100. Can't see plain smart tv on bttv-cards.c file at all...

---

### Post by Irtimid2001 on 2005-11-30
Tnx for answering, but i've done that, i already knew that :) but i don't know for sure which tuner i need to choose (so i chose nr 4). [I made a screenshot of what i have now](http://users.telenet.be/verhavertd/tv-probl.jpeg) , as you can see, it's already in color :) (tnx to stepper who explained some things in his post (link on previous page)) but it's still a little bit snow and the only channel i can see is "Cartoon network".

---

