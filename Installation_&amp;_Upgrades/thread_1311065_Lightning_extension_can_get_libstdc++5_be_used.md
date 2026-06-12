---
title: "Lightning extension: can get libstdc++5 be used"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by GGBerry on 2009-11-02
Hi everybody.

I have an issue with Karmic I didn't have with Jaunty and precedents: 

I installed Karmic from scratch. Because of work, I need a dual boot with win XP. So I was used to have cross platform programs, like thunderbird, firefox or pidgin to share the profiles between the OSes

But know for Lighning, it doesn't work: I used the Stephan Siter method:[https://wiki.mozilla.org/User:Ssitter/UnifiedLightning](https://wiki.mozilla.org/User:Ssitter/UnifiedLightning) which was working just fine for me before. Is is discussed on this post: [http://forums.mozillazine.org/viewtopic.php?p=3176895](http://forums.mozillazine.org/viewtopic.php?p=3176895) . But for this I need libstdc++5

 Karmic uses libstdc++6, what is normal, but libstdc++5 is NOT in the repositories. So I downloaded it from Debian and installed it, but it don't do the trick, my lightning still don't work (after uninstall-reinstall)

By the way, with the lightning extension from the repository which uses different packages to get ride off libstdc++5, it works like a charm, but I need this sync between ubuntu and XP.... Is there a way to use the repository extension to get install side-by-side with the windows version of the extension?

If Stephan Sitter pass through this forum: Please, help me!!

---

### Post by ^_Pepe_^ on 2009-11-02
Same here!

I've spent 2 hours yesterday with no luck. Even I've installed new beta for Thunderbird, but after that, lightning doesn't install...

I've read that it will be fixed soon, but nothing now!

I'll keep searching!

(This old bug includes karmic issue [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853))

Regards,

---

### Post by ^_Pepe_^ on 2009-11-02
Interesting...

[http://ubuntuforums.org/showpost.php?p=7981386&postcount=13](http://ubuntuforums.org/showpost.php?p=7981386&postcount=13)

I'll check at home tonight!

Regards,
^_Pepe_^

---

### Post by GGBerry on 2009-11-02
Yes, I saw this and tried it, and it works perfectly, but... no way (I think) to use this in dual-boot... If there's way, I buy it ! ;)

Nobody have an idea of how to deal with it ? Do the people that have the dual-boot xpi installed in Jaunty still have it working ??

---

### Post by ^_Pepe_^ on 2009-11-02
Oh! I didn't notice. Sorry!

Anyway, lightning extension in repositories, doesn't work either with Google Calendar syncronization extensio, that is what I exactly need. 

:-( Upset here, also...

Regards

---

### Post by GGBerry on 2009-11-02
Do anybody have an idea ?
I can see that libstdc++5 is correctly installed:
```
sylvain@sylvain-laptop:~$ ls -l /usr/lib | grep -i libstdc++
lrwxrwxrwx  1 root root       18 2009-11-02 07:14 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--  1 root root   737192 2008-05-10 01:18 libstdc++.so.5.0.7
lrwxrwxrwx  1 root root       19 2009-10-31 13:58 libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r--  1 root root   962800 2009-10-14 18:51 libstdc++.so.6.0.13
```But my lightning is still buggy. I'm starting to think that is something else... :(

---

### Post by GGBerry on 2009-11-03
Nobody, really ?

---

### Post by oscarmeyer51 on 2009-11-05
FYI - I know this is not a recent post and you may have all ready worked around it, but I reinstalled fresh with Karmic and found the same issue. 

I had restored my old folders & defaults just fine, but Lightning was not working properly for me (was on 9.04, but the new install does not have the libstdc++5 even available in the repositories). Since I had pulled over the old folders, it appears that the old Mozilla Lightning Extension was in there as well and gunking up everything. 

The steps I took to correct this were:

1) Deinstall Lightning from the Tools>Addons section of Thunderbird; restart Thunderbird (mozilla's)
2) Disable Lightning from the Tools>Addons section of Thunderbird; restart Thunderbird (from repositories)
3) Remove Lightning from the system using Synaptic; restart Thunderbird
4) Reinstall Lightning from the repositories; restart Thunderbird

And YES, only one Lightning was showing up under the Tools>Addons section.  

I only boot into Ubuntu, so I doubt this addresses your multiplatform issue, but it may aid someone else who has done a fresh install.

---

