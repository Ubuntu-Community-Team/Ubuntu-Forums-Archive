---
title: "xserver/graphics driver crash after suspend"
date: 2016-03-28
forum: Hardware
---

### Post by tony116 on 2016-03-28
After a fresh install of Xubuntu 15.10 I have an issue where after I resume my laptop from suspend I will get a black screen with blinking underscore in top left corner and eventually the login manager will come up but upon attempting to login it takes me straight back to login manager. This same issue also happened in Manjaro Linux i3 15.12 except I got a complete black screen after resume, I could change TTY to get to CLI but when trying to start another xsession with startx it would immediately go to black screen. 

To temporarily fix issue I installed Xubuntu 14.04-4 and suspend works like normal. This leads me to believe the problem is either related to the updated kernel or a problem with the newer Intel video drivers. An observation I noted between 14.04-4 and 15.10 is that in 15.10 when the login manager first displays after a boot the screen will flicker for a split second. This also was happening in Manjaro i3 15.12 but in Xubuntu 14.04-4 there is no screen flicker. 

System Info:
Alienware 15 R2 Laptop
Intel(R) Core(TM) i7-6700HQ - Intel HD graphics 530
Nvidia GTX 970m(Optimus)

---

