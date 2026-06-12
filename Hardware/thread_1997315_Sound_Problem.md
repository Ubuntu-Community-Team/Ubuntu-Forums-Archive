---
title: "Sound Problem"
date: 2012-06-05
forum: Hardware
---

### Post by MaHeR HeJaZi on 2012-06-05
Good Morning,

I'm very new user to Linux community, I'm getting used to it, though, it's very difficult for me to solve problems on my own at this moment. 

I upgraded recently my OS to Ubuntu 12.04 LTS, everything works fine as usual, then suddenly all computer sounds gone. I tried the settings and everything was alright, searched the web, then I tried  alot of solutions that I don't know why and what I'm doing.

finally it worked, latest thing I did before it work that I added this line to etc/modprobe.d/alsa-base.conf 
 options snd-hda-intel model=auto
and restarted the computer, but the problem now is the sound comes out from both speakers and headphones simultaneously when I plug  it.

thanks in advance, and sorry for long post :D

---

