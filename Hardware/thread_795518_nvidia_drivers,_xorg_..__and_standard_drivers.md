---
title: "nvidia drivers, xorg ..  and standard drivers"
date: 2008-05-15
forum: Hardware
---

### Post by adz86 on 2008-05-15
hi everybody... it's a while i'm readin this forum but just now i decided to post here since i have some problems. first of all i have Ubuntu 8.04 installed with in windows on a q6600,mb asus p5kr and video card 8800gt.. and here it's the problem...

first start everything ok... then i decided to activate the restricted drivers... and everything worked perfectly. the i found on the nvidia site the latest video drivers and tried installing them following the instructions from terminal that they suggested... all problems begun here!they installed and i had an nvidia logo at boot but after that i had the screen with all kind of artifacts,unusable. so i typed ctrl alt F1 and tried some codes found on the internet,nothing ubuntu now logs at 800x600 all messed up. then tried envy but had no luck. all installation goes well but at the end system is unusable,artifacts! only solution is to use recovery mode , which fixes the problem but.. i have no 3d, and if i try to install the normal restricted drivers that at the beginning were working nothing works now! everything is screwed up!.. my question is... how can i bring all video drivers and xorg files as they were in the beginning so i can install again the nice and normal restricted drivers??? thanx a lot to everybody!:guitar:

ah please my terminal skill are terrible so if possible no code shortcuts that i get lost :P :P :P

---

### Post by adz86 on 2008-05-16
any ideas?:confused:

---

### Post by tckrockz on 2008-05-17
Sorry cant help u i had the same problem with Ubuntu so i got tired of it n switched to windows again..:(

---

### Post by alienexplorers on 2008-05-17
Did you ever think you had to many drivers loaded.  Did you unload the drivers before loading the new ones.  Sounds like this may be your problem.

---

### Post by adz86 on 2008-05-18
> **alienexplorers said:**
> Did you ever think you had to many drivers loaded.  Did you unload the drivers before loading the new ones.  Sounds like this may be your problem.

yes i do! this is why i tried uninstalling the drivers from the synaptic(and no changes). And the problem of the too many xorg.conf, i wasn't sure if i could just delete many of them without causing even more damages this is why i didn't do it.. by the way i tried the code mv /etc/X11/Xorg1.conf.1 /etc/X11/Xorg.conf   (Xorg.conf.1 should be good because is the oldest) but from the shell (ctrl alt F1) said rw-- r-- r-- and i didn't know what to do...   thanks for all help!

---

### Post by adz86 on 2008-05-18
i uninstalled the drivers using envy ,reboot, installed drivers with envy, reboot, unusable(black corrupted screen) and only thing to do is recovery mode..

the thing i would like to avoid is to do what i did for the audio drivers.... make a new ubuntu install

---

