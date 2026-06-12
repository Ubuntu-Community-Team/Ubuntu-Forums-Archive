---
title: "Help with FGLRX!!"
date: 2004-10-20
forum: Hardware &amp; Laptops
---

### Post by xkcdmagic8 on 2004-10-20
hi guys, i did what the wiki said with my radeon 9700 pro and it worked but fglrxinfo says im running a 9500 generic! I KNOW that my card can preform better than it is now because under suse it said 9700 pro and gave me ~4500 fps in glxgears whereas i get ~3000 now! help why is it telling me im using a 9500! instructions for the love of god!:)

---

### Post by Markus78 on 2004-10-22
did you run *fglrxconfig* in the terminal? if not try this after you installed the fglrx drivers (guess you did already). now you can configure your card. the only thing is. you don't have a notebook so the issues with the touchpad are no problem when you try this. 

if you have already done this, i'm sorry in this case i've no ideas.

---

### Post by cacofonix on 2004-10-27
what driver version are you using, I have been reading that the newer versions are slower than the older ones, I would recomend the 3.9.0-r1drivers are the better ones to get. Im using 3.14.1 and in glxgears Im getting around 2000fps on my 9600xt.

---

### Post by Dracontopes on 2004-10-27
[QUOTE=nitinshantharam]hi guys, i did what the wiki said with my radeon 9700 pro and it worked but fglrxinfo says im running a 9500 generic! I KNOW that my card can preform better than it is now because under suse it said 9700 pro and gave me ~4500 fps in glxgears whereas i get ~3000 now! help why is it telling me im using a 9500! instructions for the love of god!:)[/QUOTE]
 I have the exact same problem with the same card. But I don't play games in linux (yet) so it's not a big problem to me. :)

---

### Post by HiddenWolf on 2004-10-27
To my amazement I got an up and running X from the moment I finished base-config

I just ran glrxgears, and was truely amazed

I'm running a default system. 1200x1000 like desktop size
I've got an AMD Athlon 2200+
512mb Ram
Radeon 9200se

while first I got some value's from 3000 to 7000 fps, now it is evening out at 500

---

### Post by xkcdmagic8 on 2004-10-28
even at 500fps would be a bad thing.... i can get 5000 fps on my 9700 pro and im pretty sure if ur fglrx was working or drivers were working u would get at least 2000. Is ur direct rendering enabled? glxinfo | grep rendering

---

