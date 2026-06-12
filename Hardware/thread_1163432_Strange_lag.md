---
title: "Strange lag"
date: 2009-05-18
forum: Hardware
---

### Post by hazelnusse on 2009-05-18
I am running Kubuntu 9.04 on my Dell Inspiron E1505, with 4gb or ram, and 128mb radeon x1400 video card.  I am experiencing strange delay that occurs periodically, even when no applications are running.  For example, I might be in the terminal, in the middle of typing at the prompt or in vim and all of the sudden there will be a 5 second delay between when I type and when the characters show up.  Simlar things happen in Firefox, or while browsing using Dolphin.  I can hear the hard drive spooling up when this happens and think it must be something to do with this, but I don't know how to fix it.  I previously had Debian Lenny running KDE 4.2 and did not experience this, so I feel it must be something unique to Kubuntu.  

It occurs even when I am plugged in to AC and the Power Management is set to Performance, so unless there is a setting somewhere in there that is burried, I don't know where else to look.

Any ideas?

Thanks,
~Luke

---

### Post by Dark_Stang on 2009-05-18
Well, you might want to try setting your hard drive to never stop spinning while the machine is on. If the lag is from the hard drive going to sleep this should fix the problem.

```
sudo hdparm -B 254 /dev/sda
```

---

### Post by hazelnusse on 2009-05-18
Ok, I did that and it seems like nothing changed, the hard drive still spools down, and then spools up, cycling about once every minute or two.  The weird thing is that it seems to cycle even when there are no demanding applications, but maybe it is a background process that causes it to wake up and unspool.

Any other suggestions?
~Luke

---

