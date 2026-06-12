---
title: "sound go through speakers when plugin a headphones to me laptop with ubuntu 10.10"
date: 2010-11-25
forum: Hardware
---

### Post by belaltunes on 2010-11-25
hello everyone,

i run ubuntu 10.10 on [B][B]Dell Vostro V1014 which ships with ubuntu 8.10 with it, and
it seems everything worked fine right there but i installed my first and last os i like to use ubuntu 10.10, i had some diffrent issues part of them sloved by my brother and others still stick with them... 

now my problem with the sound: when i just plugin headphones the sound keeps playing through the speakers so the port or somthing dosn't work at all.

i tried first to "upgrade alsa" in some link when i searched around the web but it killed the sound totaly for me and i lost the sound from the laptop. my brother fixed it but he couldn't fix the main problem that i can't play sound through the headphones. plus until he fixed it i just lost the sound menu from the indecator... tried to remove it from the panel and to add it again but nothin helped.

sory for my english and thanks alot if somone could just help me. :)
[/B][/B]

---

### Post by ubey on 2010-11-25
You should go configure the choice of output device
Type:
```
gnome-volume-control
```in Terminal, or click the little speaker in the upper-right corner, and then click "Preferences".
Go to "output", there you should be able to configure where the sound should come out.
Hope this helps.

---

