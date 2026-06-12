---
title: "ATI problems on Toshiba A215"
date: 2009-04-16
forum: Hardware
---

### Post by 2WhEElTeRRoRisT on 2009-04-16
I have been battling this problem for about a month now and I just can't seem to find a solution that actually works. I have had this problem with Ubuntu 9.04 and Fedora 10. I get a lot of screen flickering, so bad that I can barely watch videos. So I try to install the fglrx driver and after I do that everything crashes at the point the gdm screen should appear. I would assume this has to do with an X problem, but I am not sure. I would try to go back down to 8.10 and try that, but the only internet I have available is wireless and 8.10 doesn't support my card.

The video card is an x1200 integrated. It shows to be supported by the driver so it seems that it is just an installation problem. Trouble is I can't figure out how I am messing up the install. I'm trying to find anyone who has successfully got this card running so I can if I can't get it working. 

If there is any more information that would help just let me know. I just really want to get linux on my laptop.

---

### Post by deeperDATA on 2009-04-25
> **2WhEElTeRRoRisT said:**
> I have been battling this problem for about a month now and I just can't seem to find a solution that actually works. I have had this problem with Ubuntu 9.04 and Fedora 10. I get a lot of screen flickering, so bad that I can barely watch videos. So I try to install the fglrx driver and after I do that everything crashes at the point the gdm screen should appear. I would assume this has to do with an X problem, but I am not sure. I would try to go back down to 8.10 and try that, but the only internet I have available is wireless and 8.10 doesn't support my card.

The video card is an x1200 integrated. It shows to be supported by the driver so it seems that it is just an installation problem. Trouble is I can't figure out how I am messing up the install. I'm trying to find anyone who has successfully got this card running so I can if I can't get it working. 

If there is any more information that would help just let me know. I just really want to get linux on my laptop.

Yeah, I've got the same problem. I'm trying to figure out a workaround but I haven't found a solution in all of the blogs and forums I've visited. If I can't get a suitable driver, I'm dropping Ubuntu on my laptop. This is sad. I purchased my A215 new at the end of 2007.

---

### Post by sam1948 on 2009-04-25
i'm not sure it is the same but try taking lines from the following link
and use it step by step 
dont forget to backup u'r /etx/X11/xorg.conf before changing it

[http://ubuntuforums.org/showthread.php?t=1051571](http://ubuntuforums.org/showthread.php?t=1051571)

---

### Post by 2WhEElTeRRoRisT on 2009-04-28
I'm wondering if there is a better catalyst version that I could be using. I have tried 9.3, but it doesn't seem to work and I know 9.4 doesn't work since it dropped support. I also am wondering if I should go back to an earlier version of Ubuntu like 8.10 or 8.04 along with the older video drivers. I have the ati radeon driver working alright where there is no tearing anymore, but video performance is not optimal. Its also not a big deal, but I would like to be able to turn on desktop effects and I can't do that with the ati driver. I have just been using later versions like Ubuntu 9.04 and Fedora 10 because they support my wireless card, but both suffer with the video. I'm sure there is a way to get the wireless to work in older versions, but I just don't know if that will help my video problems. Anybody have any luck with a similar setup on older versions?

---

