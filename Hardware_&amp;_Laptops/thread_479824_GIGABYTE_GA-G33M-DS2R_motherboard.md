---
title: "GIGABYTE GA-G33M-DS2R motherboard"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by TOOOL on 2007-06-20
looking at getting a GIGABYTE GA-G33M-DS2R has any one had any luck with it, building a new pc, want to run E6600 cpu, and not sure on which motherboard to use, but have been quoted a good deal by the shop on it
cheers

---

### Post by jgrabham on 2007-06-20
Look at reviews - [http://www.newegg.com/Product/Product.asp?Item=N82E16813128053](http://www.newegg.com/Product/Product.asp?Item=N82E16813128053)

---

### Post by TOOOL on 2007-06-20
has a good review from the site posted, but more interested if it well work easily with ubuntu or if there are any problems, as the reviewers sound more like windows user's

---

### Post by skottybin on 2007-08-30
Just installed Feisty (the Alt. version download) on my system ( Gigabyte GA-G33M-DS2R) and so far so good---EXCEPT I don't have any sound coming out of the audio ports. I have an intel E4300 CPU and I'm planning some overclocking in the not-too-distant future, and I've looked into a lot of different motherboards and this is a good one for it (aside from being a good board anyway). I don't know much about codecs/drivers for ubuntu stuff but that is the only problem I'm having so far, and I expect that the solution will probably present itself soon. If anyone knows why and could help that would be cool too. The motherboard has ALC889A onboard audio--which honestly doesn't mean a whole lot to me, and I've read that it's supposed to be recognized by Linux systems as ALC885, but I have no Idea how that's supposed to help, so if anyone knows...

---

### Post by orbish on 2007-09-01
Ok well I have the board... running it with a quad 6600... having a few problems, that's why i'm on here.

with quad 6600 and the chipset of the motherboard, i researched i need 2.6.22 kernel for support, so i had to go with tribe 5 of gutsy gibbon

the good: sound is working out of the box, video is handling compiz's default effects and they look great

the bad: can't play videos... might not be a motherboard issue... but it's something with memory... probably an xorg.conf tweak, nothing major

either way, there's going to be a fix for it, that's why i'm here... good board though.

---

### Post by skottybin on 2007-09-04
UPDATE-- Got it workin' now.   I read a thread about sound problems for ALC880, which it seems had the solution to my problems for the ALC889A. Installed the right packages and even though I initially had no sound when I made the changes, I soon found out that it was because the system volume for the audio ports I needed was turned off (the individual playback volumes levels). I had already checked this before, so I'm pretty sure that this wasn't the initial problem, but it was an easily resolved issue.  Now, NO PROBLEMS.  I've watched videos, listened to music, surfed the net and streamed video, and everything is working great. Feisty Rocks!  (As a PS, I'm also connected to the internet via the ethernet port connected to my "D-Link" Brand Router which is also networked to a WindowsXP based machine, and thus far I haven't had any problems there either, although it took some time to figure it out).

---

### Post by MrGando on 2007-09-20
I also have this board, I am having a problem... the thing is that I can't get the screen to work with 1680x1050 .... does anyone know the exact integrated graphic chipset that this board has ... ???

It would help me a lot.

Thanks!

---

