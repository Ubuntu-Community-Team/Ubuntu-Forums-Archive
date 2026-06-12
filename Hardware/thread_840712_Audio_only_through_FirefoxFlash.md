---
title: "Audio only through Firefox/Flash"
date: 2008-06-25
forum: Hardware
---

### Post by chandler on 2008-06-25
(8.04) I have some mp3s and I have the xine codecs, and w32 codecs but cannot play music through Rhythmbox, Totem, XMMS, Mplayer, or Amarok.  They all seem to get to 1 sec then halt.  I tried running from terminal but no errors were thrown.  I can listen to audio through Youtube without any problems.

Any ideas?  I was thinking there may be a lock or something on the HW device but I don't know.

Thanks!

```
william@wul:/var/www$ rhythmbox /home/william/Shared/Coldplay\ -\ Viva\ La\ Vida.mp3 
william@wul:/var/www$ 

```

---

### Post by molotov00 on 2008-06-25
If you can hear sound through flash and others, then I'm inclined to suggest it is not a hardware error.

I'm leaning toward codec or some other problem. Do basic .wav files play?

---

### Post by Odrodzona-Sarmacja on 2008-06-25
All xine codecs and all w32 codecs and then you go and install all totem codecs? They hate each other. On my computer they did anyway, so I removed everything called "totem" from my Xubuntu. I have no sound (I am using only ALSA on all my players) and picture issues any more. (hint: Also on Xubuntu 8.04 you can get xmms player like in older versions was... you just need to compile it yourself ;) )

---

### Post by chandler on 2008-06-26
Yeah I can get sound to work through flash without a hitch.  But when I do, I have to kill all firefox processes before it'll work through anything else.  I guess this is a software problem then.  Woops...

---

