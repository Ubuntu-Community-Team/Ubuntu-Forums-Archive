---
title: "Will an alternate install CD get around screen resolution issues?"
date: 2008-04-29
forum: Hardware
---

### Post by fredbird67 on 2008-04-29
I'm currently running Gutsy Gibbon and tried a live CD this morning of the new Hardy Heron before I had to go to work.  One thing I couldn't help but notice is that I can't select a resolution bigger than 800x600 (I prefer 1024x768 myself), and I had this problem with both Ubuntu and Xubuntu.

Has anyone noticed this problem on the live CD and tried upgrading with the alternate install CD? (I've heard you can do this, someone correct me if I'm wrong) If so, how'd that go as far as screen resolution is concerned?

I'd like to upgrade to Hardy if I can find a good solution to the screen resolution problem that I can do without a lot of hassle.  If not, I'm thinking about possibly trying the latest Mint when it comes out next month or maybe even Foresight, or possibly sitting this one out and sticking with Gutsy until October.

Anyone tried the alternate install CD to upgrade, and if so, how'd it go?

Thanx in advance,
Fred in St. Louis

---

### Post by teaker1s on 2008-04-29
```
sudo dpkg-reconfigure xserver-xorg
```

you don't state your graphics adapter but most you can alter with above, unless intel 815 which needs a package installed

---

