---
title: "HP Pavillion DV8125 Won't Resume After Suspend - Ubuntu 11.10"
date: 2012-04-05
forum: Hardware
---

### Post by skanger on 2012-04-05
Just installed 11.10 and found that while suspending works fine, resume does not. I get a blank screen, CPU fan activity and some indicator lights but no resume. 

Of the many other threads on the suspend/resume problem it seems that graphics is behind most of it. The DV8125 I have uses an ATI Radeon Xpress 200M chipset. 

Any useful suggestions greatly appreciated!

S.

---

### Post by utnubuuser on 2012-04-06
tried the nomodeset kernel parameter?

---

### Post by skanger on 2012-04-06
> **utnubuuser said:**
> tried the nomodeset kernel parameter?
no. i never heard of it - just a beginner. 

would you explain a little? thanks!

- 

after looking up nomodeset i recalled one detail when booting up:

the monitor displays an "out of frequency" message and then booting proceeds as usual. maybe this is a clue to what's going wrong and when it happens. otherwise i have no clue what to do with nomodeset.

---

### Post by Redblade20XX on 2012-04-06
Just a quick question, do you have the proprietary ati driver or the open source one? When my HP had problems with resuming it was the proprietary driver's problem. Switched to the open source one and it worked.

- Red

---

### Post by skanger on 2012-04-06
> **Redblade20XX said:**
> Just a quick question, do you have the proprietary ati driver or the open source one? When my HP had problems with resuming it was the proprietary driver's problem. Switched to the open source one and it worked.

- Red

i guess i'm using the open source driver because i just installed ubuntu and haven't yet done anything beyond installing one graphics program - and trying to suspend and resume.

---

### Post by Mark Phelps on 2012-04-06
> **Redblade20XX said:**
> Just a quick question, do you have the proprietary ati driver or the open source one? Red

The LAST Ubuntu version that supported the ATI restricted drivers for this video card was Ubuntu 8.10 -- and since the OP is running 11.10, the answer would have to be NO.

To the OP, do NOT try to download or install any AMD drivers.  The ones installed, the default Radeon open-source, are the only ones that will work.  IF you force the install of other drivers, that will just corrupt the display, forcing you to boot into command mode to remove them, and replace them with the same drivers you already have in place.

So, if it IS the video drivers, then you're simply stuck.

---

### Post by skanger on 2012-04-06
> **Mark Phelps said:**
> The LAST Ubuntu version that supported the ATI restricted drivers for this video card was Ubuntu 8.10 -- and since the OP is running 11.10, the answer would have to be NO.

To the OP, do NOT try to download or install any AMD drivers.  The ones installed, the default Radeon open-source, are the only ones that will work.  IF you force the install of other drivers, that will just corrupt the display, forcing you to boot into command mode to remove them, and replace them with the same drivers you already have in place.

So, if it IS the video drivers, then you're simply stuck.

Do you have any suggestions as to where to begin finding out if the drivers are the issue?

---

### Post by skanger on 2012-04-09
anything, anyone?

---

