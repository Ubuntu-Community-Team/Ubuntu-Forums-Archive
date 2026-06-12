---
title: "question - ubuntu 7.04 and Compaq V3000"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by helane on 2007-03-18
have a compaq presario v3000. tried to install couple of different distr. of linux without luck. spent few days and failed to run a fully functional system on my laptop. i read that it is possible to run ubuntu 6.10 on my type of hardware.. but there seems to be some problems with wireless, headphones and graphic. i am a newbie when it comes to linux and not sure i will be able to work things out - and i cannot afford not to have a computer for few weeks as i need it for my work. . there is a new version of ubuntu coming in april and was wondering if the wireless (which seems to be the biggest problem for compaq) is going to be supported better. just trying to make up my mind - should i wait for the new distr. or install 6.10. 

appreciate any help.

helane.

---

### Post by tamagotono on 2007-03-19
It's not too bad to set up.  You will need to use the latest ndiswrapper and the windows xp driver for your network card.  The standard NVidia drivers fro NVidia work perfectly. The standby works if you use the latest bios update (but then if you try to adjust the screen brightness it kills X) and finally when you plug in headphones, it doesnt disable the built-in speakers.

This has been my experience with 7.04 with all the updates as of today.  I need to re-flash my bios to the latest version to see if the screen brightness adjustment works yet.

If you need a stable system I recommend NOT installing beta software.  I would recommend dual booting 6.10 AND 7.04 so you can play with all the latest toys but still have a stable system when you need it (just share your HOME partition)

Hope this helps

---

### Post by helane on 2007-04-09
hmm... i guess i will try the 6.10 then... and then switch to 7.04 after everything will work better then. hope i can count on your help when everything dies on me... LOL

---

