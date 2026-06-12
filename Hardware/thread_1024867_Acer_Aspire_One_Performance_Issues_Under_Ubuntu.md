---
title: "Acer Aspire One Performance Issues Under Ubuntu"
date: 2008-12-29
forum: Hardware
---

### Post by mustang on 2008-12-29
Has anyone noticed that the Aspire One is in general, all around slower than it is in Windows XP?

For example, rendering of websites in firefox is noticeably slower in ubuntu (or xubuntu---whichever DE) than it is in windows. Playing a 480p video off hulu.com will result in lost frames under ubuntu but not in windows xp. 

Is everyone else experiencing the same behavior? Are there any performances tweaks/tips anyone could suggest to boost performance in the aspire one under ubuntu?

Thank you,

Manish

---

### Post by Synx on 2008-12-29
I am also having very poor performance with Ubuntu on my AAO and ive run all the tweaks on the many wiki's.  I have not tried windows yet however.  And i am using a highspeed CF card with a ZIF adapter instead of the stock 8gb SSD and i put in an extra gig of ram.  Not sure what the deal is, but watching video on revision3 and other streaming sights is almost un-usable.  :(

That on top of the lack of twofinger scroll (working in windows) and grub/lilo issues i am having booting i may have to switch to XP, although id really like to keep ubuntu as this is the perfect pen testing environment.

---

### Post by teaker1s on 2008-12-29
AAO 150 with 120gb hard drive zero issues,could it be ssd issue. Aspire one user forums run ubuntu successfully on them

---

### Post by Synx on 2008-12-29
Its not horrid, its just not great.  Do you have any heating problems?  I am running the acerfand and its making this little thing hotter than hell.  Its quiet (edit typo) though.  Oh and the battery life on the 3cell is horrible!!!  I am only getting about an hour and a half out of this thing on ubuntu.

---

### Post by teaker1s on 2008-12-29
not suffering heat issues, we use mainly for youtube and browsing.
If you have more ram them make sure that your not using ssd to swap

use laptop mode, are you using cpu scaling as we are getting arround 2.75-3 hours


 I would recommend.
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

[http://www.aspireoneuser.com/]("http://www.aspireoneuser.com/")
and
[http://ubuntuforums.org/showthread.php?t=894852]("http://ubuntuforums.org/showthread.php?t=894852")

---

### Post by albinootje on 2008-12-29
> **Synx said:**
> Oh and the battery life on the 3cell is horrible!!!  I am only getting about an hour and a half out of this thing on ubuntu.

I got 2 hours with Ubuntu 8.04
But I've done some tweaking following the AAO Ubuntu howto, and using a SD-card for /home and I've used this powertop from Intel to shut down some background processes that I didn't need.

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by mustang on 2008-12-30
Thanks for all the responses guys.

I am using the non-SSD version (160 gb) with a 6-cell. I get around 4.5 hours of battery life.

Youtube is okay (a little choppy at first but it eventually smoothens out). CPU scaling is on because I'm using the CPU frequency monitor and it does change. The fan pretty much stays high constantly but I don't mind it---it's still fairly quiet.

I don't know what could be the source of such poor performance. Thanks for the links teaker1s but I don't see any performance related tweaks.

Are there any kernel level enhancements that could be used? Would rolling my own be of any benefit?

---

### Post by Synx on 2008-12-30
There are some good threads on the aspire one user forums on running with kernels compiled with ICC specifically for the Atom.  I have not yet tried it but am considering it.  Also, i think i am about to head out to get get a big SDHC card to dual boot vista and see how that runs.

---

### Post by teaker1s on 2008-12-30
check but I think that there is issue with 4gb memory cards

---

### Post by jayupark on 2009-03-06
anyone find a fix for the choppiness?  Firefox is driving me nuts, it takes a few seconds before you can actually click anything on the page...

I'm thinking it's an SSD issue.  I think the one in the 8GB model is a hunk o junk... either that, or Ubuntu does not work well with it.

---

