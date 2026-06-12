---
title: "Amilo Li1718 Skype - Can't get it working..."
date: 2009-07-25
forum: Hardware
---

### Post by karesz on 2009-07-25
Hi!
I'm using 9.04, and can't figure out how to make skype working. I figured out, how to make the sound out part, but the mic still don't work...

So, if anybody have experiences with this notebook, i'd appreciate his/her help. Thx in advance

ps.: If it couldn't be fixed, can anybody recommend a fine working voip, which is working on both ubuntu and windows?

---

### Post by pro003 on 2009-07-25
I  have a question for you. What's that on your avatar? :confused:

---

### Post by karesz on 2009-07-25
> **pro003 said:**
> I  have a question for you. What's that on your avatar? :confused:

Well... It's a hungarian food, called hurka (there are two mainstream types of it one made with bread and pork blood -called "véres hurka" (i've found black pudding for it in a dictionary - the darkest on the pic)- and the other with liver and rice -called "májas hurka" (liverwurst in the same dictionary - the brown) - and the third one is "kolbász" it's mostly meat, red paprika and caraway seeds). We roast them together with potato, and it is really delicios. One of my favourite foods :) Try it once! (btw three different colours, curved shape, it just happened to me that i saw the ubuntu in it :D ) We mostly eat it winter or early spring.

---

### Post by karesz on 2009-07-28
Okay, after a few days of googling, i'v managed to find a solution for my notebook. Here it is:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
You add a last line containing this:
```
options snd-hda-intel model=3stack position_fix=1 enable=yes
```

reboot, adjust the volume levels, and voila, it's ready to voip :)

(btw, it's not only a skype related problem. Ekiga, emphaty voicechat won't work to until you do this)

Solution from [here]("http://ubuntuforums.org/showthread.php?t=616845")

---

### Post by Cowboybebop79 on 2009-11-27
Hi karesz used your solution on 9.10 karmic koala and everything is working fine. Btw I'm originally from Scotland but living in Hungary now and hurka reminds me very much of Haggis and tastes great. :D

---

