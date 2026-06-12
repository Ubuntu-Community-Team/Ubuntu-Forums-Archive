---
title: "Compaq Presario V3029AU -- Sound card update?"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by sagar.1986 on 2007-11-26
HI,

Installed gutsy gibbon on Compaq Presario V3029AU and did an update. Sound doesnt work :(

I made a search and found there is a similar problem for everyone else. There are many(yeah thousands :( ) solutions but none of them have worked. However, two solutions suggested:

1. Downgrade to feisty kernel (havent done this)
2. Remove alsa and install OSSv4 (not done)

IS 2 recommended? Are all Presario V3000 users using oss for sound? 

Compaq users please help :confused:

---

### Post by sagar.1986 on 2007-11-26
Ok, so here is what I have did:

1. Installed OSSv4
        this was according to [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

    Restarted my computer, all is not well. Sound works OK if I set everything to OSS. But awn-manager doesnot start coz it cant open something in libasound which works with alsa:mad:

2. REmoved OSSv4 ,restarted, now sound works OK!!!!!!!!!!!!!!!!!!

There is something wrong here, no oss and no alsa-base. Sound works ok! , and i check with lsmod, snd_hda_intel is loaded! 

So, Lesson : Something is wrong in package alsa-base. And alsa works without alsa-base. (Are the modules present in kernel package ?)

Can someone guide me here? How do I report the bug? Can anyone reproduce this in Compaq presario laptop ?

---

### Post by nautical34 on 2007-12-10
I have a V3000 too, did the same procedure as you and the sound is working. I've rebooted a couple times so I don't if it'll last but it's looking good. This is something I've had trouble with since the release of 7.04 so I hope somehow this will work.

Thanks for the tip!

---

