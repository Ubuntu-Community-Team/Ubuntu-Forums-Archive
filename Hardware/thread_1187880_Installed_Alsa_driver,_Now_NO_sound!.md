---
title: "Installed Alsa driver, Now NO sound!"
date: 2009-06-15
forum: Hardware
---

### Post by VipX1 on 2009-06-15
I've been using Ubuntu of few months now, I have 9.04 Jaunty on a DELL M1330 with SSD drive and it's a good set-up. I'm doing an online course at present and I use the DELL to watch the tutorial on-line. However, the sound always went of after one minute ot so and I had to stop the playback and start it again to gat the sound back, just pause and then play again. I thught I'd fix this once and for all so this weekend after some research I decided I try a different driver. I followed all the steps in the sound trouble shooting page and decided and identified my driver as Alsa1.0.18rc3. Then for some reason I downloaded Alsa1.0.14 from the repository and installed that in the /usr/src/alsa. Now I've No sound! When i did the install I got an error at the end, snd-hwdep.ko, dir doesn't exist and there were a few more all from the snd directory. I installed snd and essentialLinux headers but I still got that error on a re-install of the driver. Volume control says Playback=Null and Capture=Null.
'alsamixer' in teminal output= failed error, No such directory..
'aplay -l'  output= device_list:217: no sound card found
I think the problem is that now I really do have the wrong audio driver...
I can not find alsa1.0.18rc3 to re-install it, not in the repository that I can see. I looked in [www.debian.org](www.debian.org) My audio hardware: Intel crop. 8280iH(ich8 family) rev.02

Maybe I should try the DELL.iso of Ubuntu??

I've got a video lecture thisevening when I get home so I'm leaving this here confident that the answer will be on the screen before then!!
Cherrs.
P.S. A little bit of knowlegde can be a dangerous thing....

---

### Post by hg21 on 2009-06-15
If snd-hwdep.ko, doesn't exist ( It should be in /lib/modules/2.6.***/kernel/sound/core/ where *** is your kernel version ) then alsa has not installed correctly.

I'm surprised you can't find it in a repository I had no problem. 

You might want to look at
[http://packages.ubuntu.com/source/jaunty/alsa-lib](http://packages.ubuntu.com/source/jaunty/alsa-lib)

---

### Post by VipX1 on 2009-06-15
I didn't go to work in end. It was too late by the time I finished messing with the Lap-top so I just kept on messing... I think it was too late anyway!

lib/modules/2.6*/kernal/sound/core/seq/oss

lib/modules/2.6*/kernal/sound/core/oss

are the only 2 x dir and both are empty. Does that mean the driver installed in the wrong place. I installed the 1.0.14 driver in usr/src/alsa , a dir I created...

I'm going to look in that Ubuntu repository now for 1.0.18rc3 and I'll try a re-install unless any better ideas appear..
TY, VipX1

---

### Post by VipX1 on 2009-06-15
Install alsa-driver-1.0.20 and now I'm back to where I started.
I have cracking sound most the time and when I move a volume control and also if I watch any videos on youtube the sound stop working after approx 2 minutes and I must pause and play again to get the sound back.

---

### Post by VipX1 on 2009-06-15
Just to add some more details:
The sound pops and squeaks for want of a better description like there is digital sound coming threw it or data or something! 
I installed alsa-lib-1.0.20 with no problems but alsa-utils-1.0.20 will not install
everything is ok up till:
```
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.20/alsactl'
make: *** [all-recursive] Error 1
```

I don't know if I need this part or if I have the driver in the right place
```
/usr/src/alsa/
```



The latest info is [here]("http://www.alsa-project.org/db/?f=69e6827c04529394125bc3d34ba4bedce8baba2f"), with new driver info....

---

### Post by VipX1 on 2009-06-15
Skype On.

---

