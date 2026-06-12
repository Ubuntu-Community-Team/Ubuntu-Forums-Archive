---
title: "Mic not working and general sound problems. (Asus P7P55D-E MoBo)"
date: 2010-03-23
forum: Hardware
---

### Post by jneusteter on 2010-03-23
**Here is the problem:**

The microphone on my Asus P7P55D-E motherboard is simply not working. Very confident it is a software issue.

**What have I tried:**

Well I found this bug report; [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359) Which is the only thing I found regarding my issue. I tried this command "sudo apt-get install linux-backports-modules-alsa-karmic-generic". What happened was that my front-jack speaker stopped working and the audio from my mic would come thru my speakers but not record. So I started trying some of the other commands from the bug report page and messed it up really bad. Now all my sound is messed up.:oops:

**Where I need help:**

First I need to know how turn every sound setting to the default kubuntu settings. And why the command "sudo apt-get install linux-backports-modules-alsa-karmic-generic" did not work and how to fix it.

---

### Post by aboud on 2010-04-28
same problem here .. 

sudo apt-get install linux-backports-modules-alsa-karmic-generic did help .. 
trying different setting from gstreamer-properties didn't solve it too, works under windows.

---

### Post by chicabomb on 2010-04-28
Same problem with the mic but my backports are alredy updated without my interfering, so if i dont find the soulution soon im going back to win 7,:(

---

