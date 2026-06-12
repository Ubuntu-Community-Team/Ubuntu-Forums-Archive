---
title: "Intel HDA annoyances and ALSA - Headphones and Speakers at the same time"
date: 2008-12-10
forum: Hardware
---

### Post by cplusruss on 2008-12-10
Hello, 

I've been using Linux now for about four years with a Windows box always running somewhere in the house "just in case".  Vista pissed me off enough to boycott it completely, regardless of minor things not working or software not running, etc.  I've managed to get everything working perfectly on all my systems, except audio on my Sony VGN-NR280E laptop. I've read and tried EVERY ALSA configuration, upgrade, recompiled kernels, rebooted, even talked to Intel people and Sony Tech, done the ndiswrapper stuff with the original drivers, etc. etc.  

The problem is simple, and tons of people (with HP/Acer/Sony) seem to have it:  I plug in headphones, and the sound comes out of the speakers and the headphones at the same time.  I like listening to music in public places while I work, so it's a HUGE annoyance.  There's a switch in the ALSA mixer that says "headphone" and that does nothing.  I have no idea.  Anyone have a similar problem with headphone sense?  Works fine in Micro$oft...

---

### Post by blackened on 2008-12-10
I know you said you tried 'em all, but since I had this same problem once upon a time, I figured I'd point to this one as it helped sort mine out: [http://ubuntuforums.org/showthread.php?t=806620]("http://ubuntuforums.org/showthread.php?t=806620").

Sorry if you've already tried this one and it didn't do anything for your problem.

---

### Post by cplusruss on 2008-12-10
Thanks for the quick reply man hahah even if it doesn't work, I love this forum.  

Sound or no sound, Linux rocks.

---

### Post by blackened on 2008-12-10
Ok, since my model is not that far off from yours (I have an NR385E) I figured the hardware would be similar. Quick question though: when I open up /etc/modprobe.d/alsa-base in gedit from the terminal it comes up with a blank file, but if I navigate to the folder in nautilus and open it from there, then it is full of entries. Are you experiencing something similar?

Also, what model soundcard do you have? Mine is ALC262 using snd-hda-intel model=sony-assamd in alsa-base.

---

### Post by cplusruss on 2008-12-10
> when I open up /etc/modprobe.d/alsa-base in gedit from the terminal it comes up with a blank file, but if I navigate to the folder in nautilus and open it from there, then it is full of entries. Are you experiencing something similar?

Mine comes up correctly using ```
sudo gedit /etc/modprobe.d/alsa-base
```

My card is the following: 

 ```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC262
Codec: Conexant ID 2c06
```

I actually fixed the problem *finally* by adding 

```
options snd-hda-intel model=sony-assamd
```

to the end of alsa-base, and now it sounds like ****.  Any way to install the Windows driver (which sounds perfect) into Linux, scrap the ALSA, and finally enjoy music?  Or am I doing something wrong?

---

