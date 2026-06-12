---
title: "Extremely low sound output"
date: 2005-12-05
forum: General Help
---

### Post by Speedyz2 on 2005-12-05
Hey guys,
  I'm currently using Kubuntu Breezy and after reinstalling it, I have found that my sound is EXTREMELY low. My Kmix says it is at 80%, but I can hardly hear it, If I fiddle around with the properties of my sound (such as turning it from AUTODETECT hardware to OSS or ALSA) it SOMETIMES comes on to full sound. But not always. I was just wondering if anyone else has had this problem and what they did to fix it. No sound(or extremely low sound) really sucks. I have a laptop and am using the onboard sound with it. Thanks guys/gals for any input and I hope someone can help me with this, because I don't really want to change distros just for a sound issue. Thanks again.

p.s-it has happened everytime i've installed 5.10 and can't get it to stay at a high lvl after restart, it always reverts back to near to no sound. Now I can;t even get it any higher no matter what i try. Thanks guys.

---

### Post by Hinko on 2005-12-06
I sort of had the same thing and I found that my volume was only partially controlled by 'master volume' the slide labelled 'PCM sound' actually controls it. (Don't know if that's normal, seems counter-intu&#239;tive to me). Also, try fiddling around with XMMS. It let's you select soundcards and soundservers more transparently and for some reason the volume allways works. It won't solve anything, but it will help clearify the problem.

---

### Post by Speedyz2 on 2005-12-06
Well it seems that when I've rebooted my Kmix wasnt even in the taskbar. So i loaded it up and tried the TEST SOUND option in system settings/sound and it was extremely low. i played a little with the Kmix and then looked at the HARDWARE part and its on ALSA. Should it be on that, autodetect, or OSS? Anyway I then played the TEST SOUND again and it worked, so I'm really stumped. Theres an option in there called, KDE AUTO-SUSPEND. Does anyone know anything about this? Thanks for any help guys.

---

### Post by metoo on 2005-12-06
You can always try 'alsamixer' to set the volume.
In KDE you can deactivate arts if this causes problems.
Alsa should now use dmix by default and if I'm right, it can now mix by itself.

Alsa is the kernel default sound system now and is usually recommended.

---

### Post by Speedyz2 on 2005-12-06
ok, do i have to download alsa first? sry stilla little new to Kubuntu and Linux in general...oh and if i do I have to uninstall Kmix or???? Thanks again.

as a side note, it seems to be running fine now, i went in and set the AUTO-SUSPEND option to 1 second and everything seems to work fine...but ill still try the alsa option...thanks agian

---

### Post by Warren North on 2008-03-29
Yes I have low sound output as well.
I must of done something because it is new problem.
It worked before. Bummer I wish I could figure this one out. 
I hate to go back to windows vista just to play music.
I got reg Ubuntu 7.10 on a Dell 410 xps.

---

### Post by Whiffle on 2008-03-29
Open up a terminal and type "alsamixer", it shuold bring up a text based sound control.  Use the arrow keys to move from channel to channel, M to mute/unmute, and up and down to change them.  Master is usually the one the taskbar sound controller controls, PCM controls the output of programs essentially.  I never put PCM above 77 or it distorts on mine.

---

### Post by Warren North on 2008-03-30
Yes that helps I had to tinker with the mixer.
I did not do it in terminal but that info really helps.
Also I found I have another mixer program call SigmaTel STAC9227 (OSS Mixer)
So I guess i can change device as well.
Actually some of the problems help me to learn this OS.
Thanks.

---

