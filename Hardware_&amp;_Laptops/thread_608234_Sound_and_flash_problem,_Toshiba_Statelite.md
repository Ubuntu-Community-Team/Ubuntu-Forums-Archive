---
title: "Sound and flash problem, Toshiba Statelite"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by Taleman on 2007-11-09
I have two problems with Ubuntu Gutsy on my toshiba Satellite A105-S2716

1st- Sound doesn't work, I've looked through the forums at the various post for a fix and not only o they not get the sound working properly but they cause additional problems. 

2nd- Flash on Firefox (I also tried on Opera with same results) only play for 5 seconds. For example i go to Youtube and start playing a video the first five seconds play just fine but after those five seconds it just stops where it is. it doesn't end the video it just freezes at five second then i have to click the tracker on the seek bar so that it starts playing again for 5 more second before once again stopping. 

does anyone now how to fix either of these or does anyone have similar problems?
Any help is appreciated.

---

### Post by bharris25 on 2007-11-10
you can try this, worked for me not sure I you tried it already.

Originally Posted by jekylczar View Post
i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

---

### Post by tubasoldier on 2007-11-10
I had the same issue with sound on Gutsy, I also had the same issue with sound on Fiesty when it was fairly new. As far as my laptop I've left ubuntu for opensuse, much more stable on my laptop. NetworkManager even works properly. But my desktop still bears the Ubuntu seal.

---

### Post by Taleman on 2007-11-10
> **bharris25 said:**
> you can try this, worked for me not sure I you tried it already.

Originally Posted by jekylczar View Post
i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

I previously tried adding options snd-hda-intel model=auto to /etc/modprobe.d/alsa-base
and it got the sound working but the sound would be very glitchy, any sound that was played went into a continues loop and also the Alsa volume control had  no affect on the sound. The only way to adjust the volume was using the volume control built into the laptop. It also caused a problem where the computer would freeze anytime i tried to shutdown or restart it from the GUI. so i was forced to use init 0 and init 6 instead.

I your sugestion a try, I added options snd-hda-intel model=3stac instead of options snd-hda-intel model=auto and I got the same problem with restarting and shutting down my computer but the sound still didn't work in any way.

---

