---
title: "Friends HP pavillion DV5000"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by loserboy on 2007-04-22
I finally convinced one of my friends to let me install feisty on his laptop, and mostly everything is working except wireless and his fans.

I think I found a fix for the wireless[here ]("http://ubuntuforums.org/showthread.php?t=399327&highlight=DV5000")


and I've seen a couple things about the fans, but I was hoping someone could point me to the best solution for it before I go playing around with it, preferably from someone with a DV5000 but anyone with an answer would be cool  :)

his is the one with an AMD turion 64 and the ATI 200M

---

### Post by loserboy on 2007-04-23
i'm running 32-bit if that helps...

---

### Post by firstc624 on 2007-04-23
i have this laptop as well would love it if someone had an idea of what to check

on a side note i used [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+wireless+broadcom") for wireless

---

### Post by feed_sparky on 2007-04-23
Well I have  a dv5215us and I have everything working. I used ndiswrapper with the bcmwl5.inf driver for wireless, the restricted drivers module in Feisty worked with my ATI 200m video card, and my fans have always worked since dapper. Right now I am using Debain Etch and Ubuntu Feisty and everything works in both distros. Beryl and/or Compiz are the only things I haven't tried, but don't really care if they worked or not.

EDIT: I don't like to use the bcm43xx wireless fix just because there were problems with my bcm4318, the card would just shut off and I only had 11mps speeds. If th bcm43xx doesn't work for you let me know and i'll try to remember how I got ndiswrapper to work :)

---

### Post by firstc624 on 2007-04-23
has ur lappy been unusually hot?  mine seems to warm up more than than its windows partition

thx

---

### Post by saultpastor on 2007-04-24
> has ur lappy been unusually hot? mine seems to warm up more than than its windows partition

I have a dv2000 and it seems very hot. 

If I run Beryl the Nvidia card runs around 75c and the fan never quits.

The processor cores run 36-42c and 39-46c respectively.

I'm not really a gamer but I have been playing Open Arena a bit and the  Vid card runs 101-105 the whole time the game is open and the fan jumps to high.

My left hand gets warm, I suspect this is where the GPU is located.

I wish someone would say there is a problem and it is being addressed, but I keep looking and I'm not finding anything.  I've only had this laptop a month, I saw Nvidia and HP and thought this should do well in Linux.

I may have to put Vista back on it and be owned by M$ or ebay it.

---

### Post by loserboy on 2007-04-24
> **firstc624 said:**
> i have this laptop as well would love it if someone had an idea of what to check

on a side note i used [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+wireless+broadcom") for wireless

well I haven't had a chance to get back on his lappy but as I searched around someone said there is an option in bios to tell your fans just to stay on full time and that it will bypass any sensor problems in ubuntu. Although it might eat batteries it's better than killing the cpu, could you confirm if that works or not?

thanks

also my friend says in windows his fans run almost full time anyway even when not doing anything, have you had that happen?

---

### Post by yurtboy on 2007-08-09
same here fan stays on and heat is high.
On the DV9000 this did not seem like an issue?

---

