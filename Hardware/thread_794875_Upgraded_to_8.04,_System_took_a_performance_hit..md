---
title: "Upgraded to 8.04, System took a performance hit."
date: 2008-05-15
forum: Hardware
---

### Post by F34R1355 on 2008-05-15
So I recently decided to upgrade Ubuntu to 8.04LTS from 7.10. When I ran 7.10 it was responsive, and performed great. The only issue that I had was with compiz, which seems to be a common problem with Radeon based cards, and I didn't mind having it disabled.
However, after upgrading to 8.04 I lost any kind of performance that I did have. The first thing that I noticed was that it told me that I was running restricted drivers. Which is true, because I run fglrx, I just found it a little odd due to the fact that I had run them for quite a while with no complaint. Then I go to open Firefox, and it slowly drew the window. So figuring perhaps it was still finishing the update, maybe it had a few things to run on this boot, I let that go past. Then after browsing the internet for about 3-4 minutes, I come across a flash animation (on yahoo) which brought the thing to a near standstill. Getting tired of the performance I reboot. Comes back up same problem. I then decide to run glxgears, and find that my once 4000fps is not only 30-45fps. Compiz is still off, so I know that it is not the issue.
I have made sure that I am still running fglrx.
The whole system is acting slower, not just video, but I believe that the problem stems from the video. it takes 3-4 minutes to open a video that used to seem instant.

The computers Specs are:
Amd Athlon 2400+ (I forget the core)
1GB DDR (PC2100) 2x256 1x512
Abit Nforce2 Motherboard
Radeon 9800 Pro 256MB (R350 core)
Windows on Maxtor single platter 60GB.
Ubuntu is on a Samsung 20GB drive.(Dual boot, in case you didn't make the assumption :lolflag:)

I don't think I am missing anything important. If you need more info, just let me know. If I by chance come across a solution before one is posted here, I will post what I came up with.
Thanks,
F34R1355.

---

### Post by GnuSense on 2008-05-15
Are there any processes eating up a disproportionate part of your CPU?  Try 'top' from a command line or 'htop', which you may have to install first.

---

### Post by F34R1355 on 2008-05-15
I think that it is safe to say that there is nothing big happening in the background. The highest percentage goes to xgl which is using between .7 and 4.7 CPU and .2 MEM. Gnome-Panel is the only other process that is using >0 with a .1 CPU and .1 MEM.

Thanks for the suggestion.

Edit: does htop do anything beyond top?

---

