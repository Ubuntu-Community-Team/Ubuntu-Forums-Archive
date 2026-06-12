---
title: "Home partition lost when upgraded"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by Che_Koala's on 2009-03-24
*EDIT*

Prefix is WRONG, if any admin reads this please change the prefix from kubuntu to ubuntu. Thanks and sorry for the inconvinience!

*EDIT*


Hey everyone,

I have used ubuntu on my laptop since 7.04. Around 8.04 i wanted to try and set things up a bit more convenient.

I got 150 Gig on my laptop. I need a Windows XP installation for things that wont work under ubuntu (like games n such) but I don't use it very often. So i have set it up like this now:

Windows XP : 20 Gigs
Ubuntu : 8 Gigs
Ubuntu Home: 120 Gigs
Ubuntu Swap: 2 Gigs

This was under 8.04. When 8.10 came out i tried upgrading the ubuntu installation without erasing home, but somehow the 120 are now only accessible under XP, and i use ubuntu with only 8 gigs available. I tried to make the installer use the existing home partition but it said it would format it which is not what i planned for. The main thing here, is that backing stuff up to another location is a pain for me as i am short on external storage, So i would like backing things up kept to the bare minimum.

Ubuntu home is used for Transmission, my music and photos. The latter two of those I can't afford to lose.

Now i am back at 8.04 (Compatibility issues @ 8.10) waiting for 9.04 to pop its head around the corner to re-instate everything the way i want it. my question is, how do i set it up, so i can painlessly upgrade to 9.10 when it comes out? without rendering my home partition useless? Did i do something wrong when installing? Any other ideas on how to partition everything? Maybe i can set 8.04 up so I can use it normally again and at the same time prepare for 9.04 and seamlessly upgrade when it is released?
Any light on this subject would be greatly appreciated!

---

### Post by jakupl on 2009-03-24
I would do a complete reinstall when upgrade.
Download 9.04, install and when the partition thingy comes, choose the manual option. There you can specify the /home partition and tell it not to format it. You will need to reinstall the programs that you have, but the programs will keep all of the settings.
My experience is, that it is often better to do a complete reinstall instead of upgrading. It just proves to be smoother.

---

### Post by Che_Koala's on 2009-03-24
Thats what I tried last time, was the option to not format the specified /home partition also available in 8.04? Maybe I just overlooked it, though in my memory I carefully checked for any option to *not* format, without succes.

---

### Post by jakupl on 2009-03-24
> **Che_Koala's said:**
> Thats what I tried last time, was the option to not format the specified /home partition also available in 8.04? Maybe I just overlooked it, though in my memory I carefully checked for any option to *not* format, without succes.

Well if you have 8.04 installed now, and you just want to use your 120 partition as /home than you can follow this excellent howto [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

though you can skip right to the **Using the new partition ** part.

(I have followed this tutorial many times, and I have had problems with permissions every time. If you do exactly as is says, than remember not to freak out when it does not work instantly. Just boot to recovery mode and do a ```
chmod [COLOR="DarkRed"]username[/COLOR]:[COLOR="DarkRed"]username[/COLOR] /home
``` or something like that...)

I guess you have done this before, as you already have a seperate /home partition.

---

### Post by Che_Koala's on 2009-03-24
I did create separate partitions, though this was on a new installation and thus pretty easy.

Thanks for your help!

---

