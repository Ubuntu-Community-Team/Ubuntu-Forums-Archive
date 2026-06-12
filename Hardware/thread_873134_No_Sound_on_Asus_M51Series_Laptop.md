---
title: "No Sound on Asus M51Series Laptop"
date: 2008-07-28
forum: Hardware
---

### Post by genuchelu on 2008-07-28
As the title suggests, I have no sound. Its a brand new installation of Ubuntu, I'm pretty new, so if somebody can help me diagnose the problem.

---

### Post by trigsenior on 2008-07-28
i did a google and found this post.

[http://vip.asus.com/forum/view.aspx?board_id=3&model=M51Sn&id=20080608204838687&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M51Sn&id=20080608204838687&page=1&SLanguage=en-us)

here is the link in english (not french) [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by genuchelu on 2008-07-29
I've looked [here]("http://ubuntuforums.org/showthread.php?t=753679&highlight=m51&page=3"), but his solution did not work for me... perhaps I did it wrong. I'm a noob when in comes to diagnosing hardware problems. So I would appreciate it if an expert out there would help me work this out....

---

### Post by genuchelu on 2008-07-29
I wish someone would help me...I don't wanna have to install windows...

---

### Post by genuchelu on 2008-07-29
ok thx for the help.... I'm back in vista and its going great... I finally have sound when I go to youtube..

---

### Post by DownTown22 on 2008-09-24
Check this out:

[http://ubuntuforums.org/showthread.php?t=893578&highlight=Asus+M51sn](http://ubuntuforums.org/showthread.php?t=893578&highlight=Asus+M51sn)

I have the same laptop and this worked perfectly for me.


So, basically you want to enter this in a terminal:

sudo gedit /etc/modprobe.d/alsa-base

Then add the following lines to the very end of it:

options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel

---

### Post by Crafty Kisses on 2008-09-24
What are the results of this command:
```
lspci
```

---

