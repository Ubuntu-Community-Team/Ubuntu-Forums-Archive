---
title: "Sound card not plaing in all speakers"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by zebedeeboss on 2009-09-09
Need help setting up my sound card please. Music doesnt use all speakers in 5.1 system  I assume I need right drivers

Can anyone point me to a simplified tutorial on how to dl the latest drivers for your sound card and install them.

Loving the stability - hating the complexity....

Please help

---

### Post by zebedeeboss on 2009-09-10
Shameless Bump...   :P

---

### Post by zebedeeboss on 2009-09-10
Guess I'll have to work it out myself.... lol

---

### Post by zebedeeboss on 2009-09-13
It seems that by default the surround vol is muted
solution right mouse click the speaker icon and choose open volume control
then click preferences  find surround and click check box to enable
you can now adjust the volume going to the surround speakers
you might also want to add front and centre speaker as well

---

### Post by Norman IV on 2009-09-13
Don't be so sure you have fixed the problem. I had the same problem as you, and changing the volume for the "surround" did turn on the rear speakers, but only for internet streams/music. To get actual surround sound to work right in my movie player I had to edit the Pulse Audio configuration file, I think it's called daemon.conf  (  /etc/pulse/daemon.conf file.
Set default-sample-channels = 6  -  posted by Lucky75 at [http://ubuntuforums.org/showthread.php?t=1260376&highlight=surround+sound]("http://ubuntuforums.org/showthread.php?t=1260376&highlight=surround+sound"))

All 6 six speakers would work just from turning up their volume, and speaker test worked fine, but I could not get surround in movies until I did this.

---

### Post by newsoft on 2009-09-13
Did anyone figure this out?

---

### Post by Norman IV on 2009-10-27
> **newsoft said:**
> Did anyone figure this out?

I am using 8.04 (supposedly 9.04 has GUI method to do this).

open terminal and type
 sudo gedit /etc/pulse/daemon.conf
   ( make a backup if you are worried)

there are a number of settings, they show the default values and are commented out with semicolons. Find the one called "default-sample-channels".

delete the semicolon and change its value from 2 to 6 (or whatever number of speakers you have: 5.1= 6 speakers because of the sub, so 7.1 equals 8 etc.). Save the changes. Double click the volume control icon near the top right of your screen (normally) and got to menu Edit>Preferences. Enable the volume controls for PCM Surround, PCM Center and PCM LFE (There are also plain (not PCM) surround, center and lfe; if the PCM surround controls don't work try these). Other than that make sure your application is set up to use 5.1 speaker system. This solved all of my surround sound issues, I hope it helps you...

---

