---
title: "Problems with booting &quot;Life CD 9.04&quot;"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Fraank on 2009-05-25
Hi dear Community,

Hope I don't bore you with an old "bone"/bug, but I didn't find a similar problem in the archives and I hope you will be willing to help me:

I downloaded the new 9.04 image and produced the "Live CD".
MD5SUM is correct. Unfortunately, when I wish to boot with it on my (not quite new desktop machine - 1 giga) it goes only to the questionaire ("...start right away or check for errors...") and independent from my choice I end up with a bug:
Int 14: CR2ffffb0f0 ....  Stack: c011a26e .....

First I thought something must be wrong with the CD and produced up to 3 other ones. Everytime same result. On that machine I have still installed the old Ubuntu 8.04, but several corrupted files and update/upgrade not possible any more.

If I try the "Life CD" on my Windows laptop (Vista home 32 bit) it works!

So, there I sit in the corner and I don't know what else to do. I should say that I'm not an expert - more the user type.

If you could help, thanks a lot in advance (but please stay in simple computer language - thanks).

Frank

---

### Post by ad_267 on 2009-05-25
You could try installing from the alternate CD instead. This doesn't come with a graphical user interface but it will allow you to edit partitions and install Ubuntu 9.04.

---

### Post by Kevbert on 2009-05-25
Have you run memtest86+ from the CD boot menu ? It may be that you have some suspect memory. You need to leave it running for at least 2 full passes.

---

### Post by Fraank on 2009-05-28
Thanks to "Kevbert" and "ad_267".

Unfortunately the mem - exercise didn't bring any progress. It still puzzles me why it works with a new laptop but does not with the older desktop (which has already considerable features - should be sufficient for the live CD). The same bug reporting appears when I try after the two full passes (which, by the way, didn't report any errors):confused:

The procedure with the alternate CD - I am afraid - might be a bit more complicated?

Thanks for your comments

---

### Post by ad_267 on 2009-05-29
The alternate CD install is very similar to the graphical install, except it looks a bit more scary because the menus are all text based. It isn't too difficult though. You can give it a try and post here if you're unsure of anything. If you use the manual partitioning option you can select your previously set up partitions so know exactly what's going where on your hard drive.

---

### Post by Fraank on 2009-06-04
Same story!
Alternate CD boots on new laptop but only trys but doesn't finally do it on desktop. I even don't get that far as with the live CD (choice of options - check integrity etc). It's the same desktop where I originally installed 6.06 .

But I need it on the desktop!

Now I feel cornered. No idea what to do:confused:

---

### Post by rob2uk on 2009-06-04
Maybe you could try the 8.04 LTS CD, see if that works.

Then you can upgrade to 9.04 using the update manager if you feel the need

---

### Post by pazsion on 2009-06-04
I too am having similar issues.. my dell b110 boots all version of ubuntu fine..

When i go to a pentium 2/3 or earlier.. no matter what the tests say or if i have plenty of band new ram.. The system doesnt want to load..

my error wwhere it hangs

0.116119  kernal panic - notsyncing : attempted to kill the task!

I've let it run for a bit. and no progress..

I'm gonna try and see if its the cd configureation

---

### Post by 73ckn797 on 2009-09-13
> **Fraank said:**
> Hi dear Community,

Hope I don't bore you with an old "bone"/bug, but I didn't find a similar problem in the archives and I hope you will be willing to help me:

I downloaded the new 9.04 image and produced the "Live CD".
MD5SUM is correct. Unfortunately, when I wish to boot with it on my (not quite new desktop machine - 1 giga) it goes only to the questionaire ("...start right away or check for errors...") and independent from my choice I end up with a bug:
Int 14: CR2ffffb0f0 ....  Stack: c011a26e .....

First I thought something must be wrong with the CD and produced up to 3 other ones. Everytime same result. On that machine I have still installed the old Ubuntu 8.04, but several corrupted files and update/upgrade not possible any more.

If I try the "Life CD" on my Windows laptop (Vista home 32 bit) it works!

So, there I sit in the corner and I don't know what else to do. I should say that I'm not an expert - more the user type.

If you could help, thanks a lot in advance (but please stay in simple computer language - thanks).

Frank

If you have not solved the issue this solution may help.

I ran into the same issue with 9.04. Turns out that I had switched a setting in the BIOS setting for "Memory Hole". The "BUG: Int 14:" displayed on the next attempt to boot into Ubuntu. The system would not boot from the Live CD or from the HD where 9.04 was installed. I reset the BIOS and Ubuntu boots normally.

---

### Post by Kiikun on 2009-09-14
im having the same problem with installing ubuntu server 9.04 (tried alternative too) on an old compaq 7ap195. im running the memtest now but i know ive run it before and have got no problems. the bios is very limited in its choices and none affect the memory. it does automaticly shadow the system and video bios though, so im wondering if one of the unchangeable settings are what's causing this...

oh, and i know it runs gentoo so i dont think its a 'we dont like linux' issue.

AMD Athlon 1GHz
384MB ram (128+256)
Geforce4 MX 420 AGP

---

