---
title: "ATI X1400 Laptop Video Card Battery Life"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by statictonic on 2007-01-23
I've been getting poor battery life in ubuntu compared to windows so I looked into why this could be, the Core Duo is downclocking in ubuntu like it should so that's not the problem.

What looks to be the problem is the X1400 does not downclock when the laptop is unplugged like it does in windows.  When i turned the feature off in windows my battery life dropped from 5 hours on a full charge to about 3 and a half, the same as what ubuntu gives me.

Is there a way to get the downclocking feature in the windows drivers for the ATI card working in ubuntu?

---

### Post by filoa86 on 2007-01-23
i think is not possible...

---

### Post by HITMAN39 on 2008-05-01
yes you can downclock i have the same video card that you have in a dell inspiron e1705 btw with i am using ubuntu 8.04 hardy and the newest drivers i can go into terminal and type aticonfig --lsp that will show you the power states that are available and to change them you type aticonfig --set-powerstate=1 for the lowest on my card i am using driver number 1.7.1.0-8-3:) for stuff working on this laptop i have pretty much gotten everything working if you need anything just ask

---

### Post by ipatec on 2008-05-01
is there any script that can do this automatically ?

---

