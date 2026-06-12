---
title: "soundcard/JACK"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by svc297 on 2007-06-07
This is a multi-part question:

I have just installed ubuntu studio on my dell xps m170
 here are my problems, all of which i am pretty sure are related to the sound card:

1. when linux boots it blares the start-up tone, and i have no idea how to get it quieter because everytime i start up the computer the volume levels are set to ridiculously loud.

2. i am using the stock sound card, made by sigma-tel. and while the computer recognizes it, i can only control the volume on the computer using the alsa controls. 

3. when i use the jack connection manager, it doesn't recognize my sound card. it only has input/output options for midi. i, in fact, don't use midi for recording or playback. as crude as it sounds, i use the 1/4" plugs in my built-in sound card. so, i guess i want to know how i can get jack and its dependent programs to recognize my sound card.


i put this platform on my computer so that i would have an easier time recording, and i'm hoping that i can get these problems resolved so that that happens.

thanks in advance.

---

### Post by phyrewall on 2007-08-24
1. Will be fixed by #2. Once volume is set, it should stick at last volume set. If not, set the volume and then save the session. 

2. - Right-click the Volume Control applet on the upper right taskbar, select "Preferences".
    - Scroll down and select "PCM"
       If "PCM" isn't available, right click on the volume control applet, select "Open Volume Control" and then "Edit" > "Preferences" > Check "PCM"
    - Now the Volume Control applet will control the volume.

3. I'm afraid I don't know Jack. ;)

---

### Post by christhemonkey on 2007-08-24
Jack should recognise your soundcard...

Try running it from a terminal like this and post any output:
```
jackd -d alsa 
```

---

