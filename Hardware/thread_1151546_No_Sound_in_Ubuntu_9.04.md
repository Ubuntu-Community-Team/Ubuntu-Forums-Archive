---
title: "No Sound in Ubuntu 9.04"
date: 2009-05-07
forum: Hardware
---

### Post by gsiddardha on 2009-05-07
Hi, 

i bought a new laptop - Dell Studio 1555.
But i am finding lots of problems after installing linux (Ubuntu 9.04) in it.
I am not able to hear even small sound. (In windows, the sound quality is very good.)
I don't think it is recognising the video drivers also because when i open the display configuration window, it is using the proper resolution but it is saying that display not detected.

plz help me.
i have been trying for many days. and i am not able to hear even a single song in it.

plz help

thanks,
G.Siddardha

---

### Post by Offramp on 2009-05-07
Hi,

I am also having the same problem with the same laptop - sound worked in 8.10 but not in 9.04.  I am a little further down the track with trying to find a problem and believe it is related to the ALSA driver. I have upgraded to the new version (still no luck) but am getting closer to a solution.  To help me out could you post the results of the following commands:

```
dmesg | grep hda
```

and the first few lines of 

```
cat /proc/asound/card0/codec#0
```

Cheers

---

### Post by Offramp on 2009-05-08
Hi,

I now have my sound working in Dell Studio 1555.  I have been following lots of false leads, and thought I had tried this before, but for I laugh I added

options snd-hda-intel model=dell-m6

to 

/etc/modprobe.d/alsa-base.conf 

and then sound worked.  I realised that I had last tried this with the default driver in Jaunty (1.0.18rc3).  My suggestion then would be to upgrade to the latest driver ([here]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel#Introduction_for_HDA_Intel_soundcard")), add this line to the alsa-base.conf file and reboot.

Cheers

---

### Post by gsiddardha on 2009-05-17
hi,

thank you very much dude..
sound is working very nicely now..

bye

---

### Post by Fastjack77 on 2009-05-21
OMG! It's working!

Initially, I tried what you did, but it didn't work. The problem is that I screwed up my ubuntu so bad to make it work that I had to reinstall it.

But after a clean install (Ubuntu 9.04 AMD64), it worked like a charm!

Thank you so much for the info! It's much appreciated!

---

