---
title: "I have Windows XP and a Ubuntu Disc &gt;&gt;&gt;"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by stormypenny on 2009-03-06
I installed the Ubuntu disc, but it won't load after I sign in? The screen turn orangeish and then it stops there. Help please. Thanks !!!

SP

---

### Post by LegendofTom on 2009-03-06
First try ctrl-alt-backspace to stop X, then if you get a terminal type "dpkg-reconfigure xserver-xorg".

---

### Post by Bölvaður on 2009-03-06
> **stormypenny said:**
> I installed the Ubuntu disc.....

Do you mean that you put the cd into the cd tray?

If so there are few options what may have gone wrong.

1. you have too little ram. you need about 512mb to start the live cd
2. the cd was burned on too much speed which may have caused data corruption on the cd.
3. while downloading there may have been data corruption. it is possible to check by a thing called "checksum" which checks if there has been data corruption or not.
4. you have extremely old cd drive (we are talking 10 years old or more) and it doesnt.... do it somehow... dunno why. few people I know have had this, including me.

---

