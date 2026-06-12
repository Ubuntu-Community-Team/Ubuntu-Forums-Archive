---
title: "No Sound on My Laptop"
date: 2010-04-04
forum: Hardware
---

### Post by r352alit on 2010-04-04
Just installed (Newbie on Testing Mode) Ubuntu 9.10 desktop edition on Toshiba Satellite J11, after up date it there is no sound on my laptop. Already check on Ubuntu old laptop document section, but the Toshiba Satellite J11 is not on the list.... !! ALSA is already installed, but still no sound... 
So, anyone or someone can help me...? because currently right now i am downloading the Ubuntu netbook remix version that took 3 days straight....!!!! 


Thanks for the reply and the enlightment.....

---

### Post by mörgæs on 2010-04-06
There are many important improvements in the sound in 10.04, and rather than fighting with 9.10 I would go for the new one:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Though being in beta (the formal release will be at the end of April) it is a very stable release, at least on all machines where I have tried it. You could boot as a live CD and see how it behaves.

---

### Post by lidex on 2010-04-09
Go here to debug karmic sound issues:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Don't forget to check mixer levels in alsamixer as they do get muted. In a terminal="Applications>Accessories>Terminal"
```
alsamixer
```

---

