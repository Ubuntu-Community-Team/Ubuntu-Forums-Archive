---
title: "update train-wreck"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by short4lif2 on 2008-12-03
I have a ThinkPad laptop that was running ubuntu 8.04 with gnome, and it worked wonderfully for a long time.  I was using it as my primary operating system, and was waiting to upgrade.  I finally decided to take the plunge, but while the update was working, I got an error regarding python-bittorent.  It said that it couldn't install the package and the upgrade was stopping.  When I restarted, gnome was GONE.  In fact, I was greeted by kdm without gnome in the sessions list.  Can anyone tell me what on earth happened to my computer?  I am currently running sudo apt-get install ubuntu-desktop, but i don't know how to get rid of KDE and xfce.  any ideas? (i have 1 gig of space left and this is crucial)  Thanks in advance

---

### Post by taurus on 2008-12-03
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by short4lif2 on 2008-12-03
This is why i love these forums.  Thanks so much for your help

---

### Post by short4lif2 on 2008-12-03
Another interesting development.  It seems that my sound died after the update. I tried testing with the different sound playbacks and none of them worked.  What might be wrong?

---

### Post by short4lif2 on 2008-12-04
any ideas?

---

### Post by taurus on 2008-12-04
What kind of soundcard do you have?

```
lspci
```

---

### Post by short4lif2 on 2008-12-04
The best information i could find on this based on my make and model was the following

Audio

    * Audio output type Sound card
    * Audio codec CX20549
    * Audio output compliant standards High Definition Audio
    * Audio Input Microphone
Somehow there is no specific information available on this.

---

