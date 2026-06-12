---
title: "Hardy very slow with WUBI, slower than I read is common"
date: 2008-09-18
forum: General Help
---

### Post by jammadave on 2008-09-18
Hi all.

Got Hardy running via WUBI on my girl's computer - now it's running so slow she wants me to strip and install just Ubuntu (probably because I told her that there can be slowness due to WUBI overlaying Ubuntu on the Win filesystem).

But I want to make sure that's what's wrong, first, because a total format and install is a big deal.   She's running SLOW.  Like, several seconds from click to action for ANYthing, lots of "i'm thinking" greyouts, the whole nine yards.   Even Terminal can take 10 seconds or more to open, and that's the lightest-weight thing I can think of.   Oh, and even the system menus on the top panel take their time to open.

I ran Top a few times and noticed that Firefox was by far the biggest culprit, at some 34% CPU.  Other stuff like Compiz was hitting 1-2%, no biggie.  I *did* notice this morning that firefox was taking up cpu in Top, but it wasn't actually open - so I killall'd its processes to be safe.   When I opened firefox again it was pretty low in activity.

The bigger thing I saw in Top was that MemUse was huge!  something like 375MB capacity with 370MB used!   I have NO idea what THAT is about.

Will a clean install sort this out?  I'd rather do that, I think, than LVPM.   The computer in question is a Dell Dimension 2400 I believe, and I don't have the CPU/RAM specs handy.


:confused:
Thanks!
Dave

---

### Post by Bakon Jarser on 2008-09-18
Having ubuntu with firefox open taking up over 300mb of ram doesn't surprise me at all.  It sounds like you might have a slow computer.  You may want to try xubuntu.  It is much more lightweight then ubuntu.  Otherwise you might want to consider adding more ram.  ram is cheap these days but you'd have to look up your dell online and make sure it can take more ram and make sure you get the right kind.

---

### Post by jammadave on 2008-09-18
> **Bakon Jarser said:**
> Having ubuntu with firefox open taking up over 300mb of ram doesn't surprise me at all.  It sounds like you might have a slow computer.  You may want to try xubuntu.  It is much more lightweight then ubuntu.  Otherwise you might want to consider adding more ram.  ram is cheap these days but you'd have to look up your dell online and make sure it can take more ram and make sure you get the right kind.

well if i remember right, the mem use was still that way with ffx shut  down!

---

### Post by Orlsend on 2008-09-19
There is something to rigth there I oepn like 20 tabs when start firefox and the max I have seen is 67MB used by FF.

I have more than 25 Add-ons and tons of settings that should make FF memory hog yet it those not.

---

### Post by Bakon Jarser on 2008-09-19
> **Orlsend said:**
> There is something to rigth there I oepn like 20 tabs when start firefox and the max I have seen is 67MB used by FF.

I have more than 25 Add-ons and tons of settings that should make FF memory hog yet it those not.

My firefox is currently using 70mb with three tabs open.  I'm guessing one of your add-ons is adblock which helps a ton with memory and cpu and i'll go out on a limb and say another one of your add-ons is noscipt which also helps a ton with memory.  Memory usage really depends on the pages and their content.  When I visit pandora for a while I get up over 100mb.

---

### Post by Orlsend on 2008-09-19
> **Bakon Jarser said:**
> My firefox is currently using 70mb with three tabs open.  I'm guessing one of your add-ons is adblock which helps a ton with memory and cpu and i'll go out on a limb and say another one of your add-ons is noscipt which also helps a ton with memory.  Memory usage really depends on the pages and their content.  When I visit pandora for a while I get up over 100mb.
You are correct :D

---

### Post by cyberkarma on 2008-11-16
I know this thread is a old, but I just installed Ubuntu 8.10 with Wubi on my PC, and it is behaving exactly as jammadave said. It cant be memmory, as I have 896 MB RAM on my laptop - the rest of the 1 GB RAM taken up by video. My laptop has AMD Turion 64 X2 Mible Technology TL-58 processor at 1.90 GHz, which run my Windows XP and several application very well. This is a HP laptop without any tampering done on it - the fact that XP run very well supprts it. It is just the Ubuntu on Wubi is slow. It is very very slow that it takes ages to open up any window. Infact it took me good 3 hours to install Ubuntu. Dont know if anyone else has this issue.

---

### Post by redscorp on 2008-11-25
What about defrag state of your HDD?

---

