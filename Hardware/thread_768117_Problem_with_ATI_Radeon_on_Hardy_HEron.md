---
title: "Problem with ATI Radeon on Hardy HEron"
date: 2008-04-26
forum: Hardware
---

### Post by nikiu on 2008-04-26
I used to work fine with Gutsy, with compiz effects enabled. Now, I upgraded to Hardy Heron and my Ati Radeon 9600 (laptop Dell Inspiron 8600) seems to work OK but the graphics are not fast enough, I see the effects going like sluggish. And also, when I try to watch a movie in full screen, it seems like I am watching a DVD on a Pentium II, if you know what I mean. It is like the GFX Card is working with 1/4 of its power... :( Any help?

---

### Post by nikiu on 2008-04-28
I tried also with clean install of Hardy Heron and it seems to work better but still I have problems with the frame rate. Any help?

---

### Post by sensui on 2008-04-28
And. Had you seen a white screen when you enabled COMPIZ?

because of it, I've been hesitating to install Hardy since I had seen a terriable white screen on Hardy Beta

---

### Post by markcgriffiths on 2008-04-28
I have the same problem, Have you installed libdvdcss or something like that?  At least that speeded up my DVD playback.  Basically turning off Compiz when watching videos is the best solution.

I have not seen any white screen, I have a x300 card though.

---

### Post by coleki on 2008-04-29
I am also having problems with my Radeon 9600 on Hardy.
When I try to use the restricted driver for ATI, I can only boot in low-res mode. When it does boot in low-res mode, I lose the ability to go back to widescreen resolutions (the only options are then 800x600 and 640x480).  The only way to get the resolutions back is to overwrite the xorg.conf with one that I configured by using the Gutsy liveCD.

Of course, this means no graphics acceleration - no desktop effects, etc.
Has anyone with the same hardware been able to get this to work?
Relevant lines from my lspci:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

Any help would be greatly appreciated.

---

### Post by nikiu on 2008-04-30
Trying to figure this problem out, I found that everything comes back to normal when I disable Advanced Desktop Effects (Compiz). I tried to disable the plugins one by one but I couldn't find where is the problem. Also, I don't get low framerate with the DVDs only, I get it with the screensavers and whatever video I try to play in full screen mode. 

I don't have any problem with white screens or whatever. My resolution is fine 1200 x 800 :|

---

