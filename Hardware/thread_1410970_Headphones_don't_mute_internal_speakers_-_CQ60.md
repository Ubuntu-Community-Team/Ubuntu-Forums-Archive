---
title: "Headphones don't mute internal speakers - CQ60"
date: 2010-02-19
forum: Hardware
---

### Post by jjjjeremy on 2010-02-19
Although this is an old problem, none of the various solutions work on my Compaq CQ60. I understand that this should be a hardware issue, that the speakers should be physically muted when the headphones are plugged in, but they aren't. It works in Windows 7 perfectly though. 

alsamixer doesn't have "Headphone Jack Sense" to unmute, and there isn't a switch in my sound controls either. "amixer -c 0 sset 'Headphone Jack Sense' unmute" doesn't work either, because there is no "Headphone Jack Sense" in alsamixer.

I've also (I think) updated to the newest alsa drivers, but I may have updated to the newest alsa drivers from 2007, because I was following an old post.

I've also tried editing the last line of some alsa.conf file, which didn't work, but that might be because I wasn't sure which model=XXXX to use.

From all my fiddling, I remember that I have a Conextant sound card, and I remember reading that Conextant doesn't provide such and such information to Alsa, which may make my problem unfixable.

I've been working on this for a couple weeks now, and I would really appreciate if someone could properly take me through the steps of diagnosing the problem. Most of the threads I have read (here and around the internet) have been shots in the dark, and I'm a bit sick (and scared) of typing random things into terminal. I have seen plenty of solutions for plenty of other laptop models, but none for mine yet.

I appreciate the help in advance.

---

### Post by jjjjeremy on 2010-02-19
bump

---

### Post by jjjjeremy on 2010-02-21
bump

---

### Post by jjjjeremy on 2010-02-28
anything?

---

### Post by Speakstofei on 2010-05-03
I know its been a couple months.  I'm hoping you found a solution.  There has been several other posts regarding the Conexant Sound card on the CQ60. I'd hate to send you to the same dead end that I've been thrown into but there are several other posts regarding this same computer.  Although this post is pretty much identical to yours.

[http://ubuntuforums.org/showthread.php?p=9228339](http://ubuntuforums.org/showthread.php?p=9228339)

---

### Post by saiganeshb on 2010-06-13
bump.. I have been searching for weeks on this..I have  a conexant cx20585 card as well  which just doesn't mute the internal speakers .Looks like it may take a while for whoever interested to take note of this. Hope it gets fixed in ubuntu 10.10 :confused: .
I even tried this painful process but of no use:
(my laptop model is lenovo)
I couldn't find conexant 5069 or conexant cx20585(which were the codecs installed in my laptop) in the list so I decided to search in all lenovo specific models instead.I am not sure if this may help you.
```

zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz|grep "lenovo" >file.txt

```and try each option in that txt file in the last line containing 'options snd-hda-intel model=' in
```

sudo gedit /etc/modprobe.d/alsa-base.conf

```I am sure this is a pathetic attempt,but I guess i had too much time to waste one day .
Anyone familiar to do this with a script btw?The only problem is we have to re-boot each time an option fails and stop when it works( if it really does).

---

### Post by saiganeshb on 2010-06-14
solved : [http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

---

### Post by googeek on 2010-06-15
> **saiganeshb said:**
> solved : [http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)



This totally worked for me! thank you soooo much!

---

### Post by spiderman05 on 2010-08-17
> **saiganeshb said:**
> solved : [http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

Thank you very much for this solution. It also works on Toshiba C650D which uses a Conexant CX20585 chip. I have spent hours reading forums and playing with the alsa config file.

---

### Post by Twiztid Anthrax on 2010-08-18
eh so many fixes yet i have a g60-530us hp notebook, with this problem'

---

### Post by djd2982 on 2010-10-12
Thank you, thank you, and thank you!

---

