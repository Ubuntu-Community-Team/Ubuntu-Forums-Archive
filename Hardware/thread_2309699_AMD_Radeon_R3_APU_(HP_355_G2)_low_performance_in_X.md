---
title: "AMD Radeon R3 APU (HP 355 G2) low performance in Xubuntu 15.10 vs. Windows 7"
date: 2016-01-12
forum: Hardware
---

### Post by poomex2 on 2016-01-12
Hi everybody, I'm new here ):P

I've recently bought a new HP 355 G2 and installed Xubuntu 15.10 on it right away, as well as Windows 7 in dual-boot. I decided to upgrade to the proprietary drivers from AMD immediately. Unfortunately, when I started installing more demanding 3D games, I've noticed the performance in them was quite mediocre in Xubuntu. I decided to install the Unigine Heaven benchmark to test performance in both the installed system. The results were quite surprising - with the exact same settings, using OpenGL in both instances, the FPS count was DOUBLE in Win7 (12.9 avg) than in Linux(6.3 avg). 

I reverted to the open source drivers but my system became a nightmare - Compiz lagged horribly and Heaven just showed a black screen. 

After hours of googling, I finally discovered that I had to remove all fxglr packages and then add the Oibaf and Xorg-Edgers repositories. That fixed the overall laginess, but the performance in Heaven was identical to the proprietary drivers. I also discovered that my laptop was getting MUCH hotter in Windows, and the fans started running at high speeds, while in Xubuntu, they stayed pretty much at constant idle speed and not much hot air was pumped from the inside. So after many more hours of trying different tiny fixes and no results I'm asking you guys for help, so I can continue to enjoy gaming on an open-source system ;)

Thanks in advance!

---

### Post by poomex2 on 2016-01-13
Bump.

---

### Post by Yellow Pasque on 2016-01-14
The results aren't too surprising to me, especially given the benchmarks Phoronix does:
[http://www.phoronix.com/scan.php?page=article&item=amd_windows_wins&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_windows_wins&num=2)

The only thing that surprises me about your results is that Catalyst Linux isn't a bit faster than the open source ones on such a new GPU.

---

### Post by mastablasta on 2016-01-15
> **Temüjin said:**
> 

The only thing that surprises me about your results is that Catalyst Linux isn't a bit faster than the open source ones on such a new GPU.

it actually is. the catalyts was installed to current kernel. where FOSS driver was initially hoorrible. upgrading the FOSS drivers with a PPA solved the issue. so if he used beta catalyst on newest kernel and it should be better or maybe also same.

to the OP - for games it is better to stick with Windows. Linux drivers are still is worse than Windows version. maybe they will fix them. but just when they do kind of imporve them they also move them to legacy (after 3 or 4 years) and proprietary verison is suddenly no longer available in Ubuntu. so in the end one is suck with opensource in Linux (at least with AMD). the only good news is that AMD helps opensoruce developers with the drivers.

---

### Post by poomex2 on 2016-01-15
Thanks for the replies. I guess until better drivers come out I'll stick to Linux for the older and least demanding games, and use Windows (which I don't really like very much) to play the newest titles.
Cheers. :D

---

