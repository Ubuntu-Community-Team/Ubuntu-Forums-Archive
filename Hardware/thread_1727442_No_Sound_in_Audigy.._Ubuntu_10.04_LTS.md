---
title: "No Sound in Audigy.. Ubuntu 10.04 LTS"
date: 2011-04-12
forum: Hardware
---

### Post by Black Pete on 2011-04-12
I've been using Ubuntu for some time now (with no problems), and today i installed some recommended updates, without even looking at them, as i do most of the days.
Then the current safety fell and everything was shut down. I had obviously to restart the system..
but then i realized that i had no sound..
i checked all my settings, seemed fine. I restarted my PC to check the sound card in windows.. then the USB wireless mouse and keyboard were shutting off by the time i was in the OS selection screen on startup, so every time i couldn't change my option, and was logging in to UBUNTU were everything worked fine..
i unplugged a USB dock for an iPOD my sister had connected. 1,2,3 restarts, everything is ok.. except the sound card.. this remains silent.. i checked it on windows and it plays fine.. anything..

So i searched for answers inside the fora, followed almost any suggestion but still nothing...
my card is recognized.. so far i've all the necessary drivers installed..
the card must be a soundblaster audigy (cheap model), and the chipset number is: CA0106
i tried the Alsa mixer.. everything is ON!
i followed almost all the moves mentioned in this thread but still nothing: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

any help out there?
thanks a lot
B.P.

p.s. just for time's sake:
i'm using (?) kernel: 2.6.32-30-generic
Also, in ```
 lsmod | grep snd* 
``` there wasn't any reference to snd_hda_intel. I had to load (?) it with ```
 sudo modprobe snd-hda-intel 
```

---

### Post by Black Pete on 2011-04-12
i just noticed, that when playing an mp3 file for testing reasons, the equalizer on the Sound menu blinks according to the rhythm.. so the beat is recognized..
my problem must be somewhere on the output.. after the processor of the card, which is installed and working.. I remind to anybody reading that i do have sound in windows..

Also, i've plugged-in and out the jack several times, and i tried all the other input holes just for.. no serious reason (knowing their use).

pfff.. this is really frustrating
:confused:

---

### Post by Black Pete on 2011-04-14
So i''ve run the ALSA information script and this is the URL i get back:[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR][http://www.alsa-project.org/db/?f=1cb0168b66d7dbea79d26a1476ca89f0ec6818e2](http://www.alsa-project.org/db/?f=1cb0168b66d7dbea79d26a1476ca89f0ec6818e2)

maybe anyone can give me a hint about this bloody problem..
thanks a lot
B.P.

---

