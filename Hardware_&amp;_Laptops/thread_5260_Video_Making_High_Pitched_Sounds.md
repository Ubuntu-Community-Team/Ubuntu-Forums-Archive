---
title: "Video Making High Pitched Sounds"
date: 2004-11-17
forum: Hardware &amp; Laptops
---

### Post by d0gbert on 2004-11-17
I have a Dell Inspiron 8100 w/ Geforce2 Go video. I'm running at 1400x1050 resolution.  Normally I listen to streaming audio when using the computer so I don't hear a lot of other sounds.  

Today my audio stream stopped for a few moments, and was long enough for me to notice a high-pitched "whine" coming from my notebook and is just barely audible.  Initially, I couldn't tell if it was my harddrive or my video adaptor because it seemed like it would change frequency when my hard drive would click (I know the clicking is normal).  The more I listened, the more it sounded like it was coming from more towards the direction of the video output.  So I'm pretty certain it is my display adaptor.

Anyway, a couple of days ago I installed the nvidia-glx, nvidia-kernel-common and nvidia-settings using synaptec.  Everything appears to work great.  It's just that high-pitched whining sound!  IMO, It sounds like the video adapter is being pushed pretty hard.  

Anybody encountered or heard of this on a notebook?  Are there any settings / configurations I should be looking at?  Should I consider this "normal"?  Or should I contact nvidia?

Thanks!
d0gbert

---

### Post by poptones on 2004-11-17
[QUOTE=d0gbert]I have a Dell Inspiron 8100 w/ Geforce2 Go video. 

Today my audio stream stopped for a few moments, and was long enough for me to notice a high-pitched "whine" coming from my notebook and is just barely audible. [/QUOTE]

Does your notebook also have the MCP-T (audio/firewire) chip in it? Does it use the MCP AC97 audio controller? I ask this because I spent weeks looking for a mini-atx motherboard with that feature that also supported dualhead video and ended up with the only one (a shuttle motherboard) that has all this. Now I'm really, really regreting it because the linux drivers suck soooooooooooooo bad for that device. I've had a lot of digital audio design experience and I'm pretty sure I know what's causing it, but without documentation on the hardware it's impossible for anyone but nvidia to fix it. My ten year old twenty dollar ensoniq audio pci card beats this shiny new motherboard hands down on audio performance. The graphics are nice enough, but an all-in-one solution is important to me and now it's clear that even my old S3 was a better all-around motherboard.

Anyway, all that effort, now I'm going to end up using a $20 USB dongle for audio. Maybe this would help you as well.

---

### Post by Mischa on 2005-01-16
[QUOTE=d0gbert]I have a Dell Inspiron 8100 w/ Geforce2 Go video. I'm running at 1400x1050 resolution. Normally I listen to streaming audio when using the computer so I don't hear a lot of other sounds. 
 
 Today my audio stream stopped for a few moments, and was long enough for me to notice a high-pitched "whine" coming from my notebook and is just barely audible. Initially, I couldn't tell if it was my harddrive or my video adaptor because it seemed like it would change frequency when my hard drive would click (I know the clicking is normal). The more I listened, the more it sounded like it was coming from more towards the direction of the video output. So I'm pretty certain it is my display adaptor.
 
 Anyway, a couple of days ago I installed the nvidia-glx, nvidia-kernel-common and nvidia-settings using synaptec. Everything appears to work great. It's just that high-pitched whining sound! IMO, It sounds like the video adapter is being pushed pretty hard. 
 
 Anybody encountered or heard of this on a notebook? Are there any settings / configurations I should be looking at? Should I consider this "normal"? Or should I contact nvidia?
 
 Thanks!
 d0gbert[/QUOTE]
  i have the same problem with my dell inspiron 8200. have not found out why... let me know if you know :)
 also, as long as you run 'vumeter -r', it is silent again [img]http://www.ubuntuforums.org/images/smilies/icon_question.gif[/img]
 but then again that might be because it's using a lot of cpu: 93.4 ...
 
 anyony

---

### Post by scoot1212 on 2005-03-14
I had this same problem myself.  After poking around my default color depth was 24 and I changed it to 16 and my whining has gone away completely.  My laptop is now usable with the gui.  I hope this fixes your problem too.

Scott

---

### Post by eternity on 2005-03-14
I had a similar problem with my previous laptop, a Dell Inspiron 4100 with same configuration. I could only hear the whining when computer was idle. The sound got quieter when i used cpufreqd to decreased the cpu frequency when the laptop was idle.

---

