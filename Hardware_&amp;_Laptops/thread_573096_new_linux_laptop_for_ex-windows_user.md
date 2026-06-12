---
title: "new linux laptop for ex-windows user"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by Reid.Wall on 2007-10-11
hey,
so I'm so incredibly sick of windows, I'm currently working on using Ubuntu (fiesty), but still running it in Wubi (just getting some hdd problems sorted).  Anways, I'm buying a new laptop in December.  What would you recomend for Linux? I was thinking about the Thinkpad T61, basically I want something powerful, but that is fairly small, but I want to sacrifice as little performance as possible for the size (I'm not looking for a thin and light, just something smaller than my dell latidude d810.  Also, do you have any websight suggestions for someone like me who is fairly new to linux (I'm not an idiot, I can keep a windows machine running well).  

thanks for your help

---

### Post by MaximusTG on 2007-10-11
Do you plan on playing games with it?If not, your best bet is a laptop with an intel GMA videocard. I'm not sure which wireless cards work best but I believe that the Intel wireless cards also work fine.
I have a broadcom wireless, but setting that up with ndiswrapper was really easy.

You should probably look for a laptop with Intel Centrino technology, since that guarantees that all components are of Intel make.
They are quite expensive though..
Good luck!

---

### Post by gibbsnich on 2007-10-11
The most important thing in my eyes is wireless. It should work right out of the box. That's important because if you have other problems (maybe setting up another hardware-component) you can get google's support for finding help and you don't have to sit near your router because you need to use cable.
The good thing is that Ubuntu supports most wireless cards out of the box: Feisty had no problems with my Intel BG2200 card, the Atheros card from my friend's laptop also "just worked". Gutsy should be even better supporting various wireless cards. Just check the ubuntu forums before you buy your new laptop. 
One thing I'd also find important: Watch out that your new laptop has a real hardware-switch for turning on your wireless. Then you don't depend on your laptop's manufacturer (or some nice guy who happens to have the same laptop and has enough knowledge) to support linux and offer a software module for you to actually switch on your card. For example, I had really a hard time figuring out that I need the fsam7400 module to enable my wireless card on my laptop which doesn't have a hardware switch but that was back in 2005, now Ubuntu supports it out of the box...
I never had any problems setting up Ubuntu on machines that have ATI or Nvidia graphic cards. The open drivers that ship with Ubuntu usually just work (maybe without 3d acceleration), and getting "original" drivers installed when you're connected to the internet nowadays is no problem anymore.

HTH!

Michael

---

### Post by Whiffle on 2007-10-11
I think a thinkpad would be a fine choice.  I'm running gutsy on a T43 and the majority of things work right away, such as wireless, bluetooth and power management.  I need to do some tweaking to get the S-video out working, but other than that I couldn't ask for more.

---

