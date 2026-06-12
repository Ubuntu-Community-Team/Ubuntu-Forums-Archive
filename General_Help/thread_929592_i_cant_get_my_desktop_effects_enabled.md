---
title: "i cant get my desktop effects enabled"
date: 2008-09-25
forum: General Help
---

### Post by jokakid on 2008-09-25
i run compiz and this is wat i get

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:002d (rev 15) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by loomsen on 2008-09-25
OK, as you obviously have a VGA-Controller... I'd instantly call Nintendos customer support and claim my money back if I was you!

---

### Post by jokakid on 2008-09-25
:lolflag:

---

### Post by justsomedude on 2008-09-25
Please post the output of 
```

glxinfo | grep render
```

---

### Post by j.miller565 on 2008-09-25
what kind of card are you using and have you installed the drivers for it?

---

### Post by jokakid on 2008-09-25
direct rendering: Yes
OpenGL renderer string: RIVA TNT2/AGP/SSE2

and i believe i installed them

---

### Post by j.miller565 on 2008-09-25
hmm interesting how old is the card? I'm not to sure what the system requirements are for running Compiz, but I'm going to have a look around now.

oh yea try Compiz--Check. It can be found here: 

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
and
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

this may help

---

### Post by loomsen on 2008-09-25
Riva is for pretty old cards as far as I know. When I once compiled rivafb as a module into a custom kernel I wasnt able to install my actual driver afterwards. So, if your card aint older than, lets say, Bart Simpson, you should get rid of it and try one of the legacy drivers instead. Still it would be useful to tell sth about your hardware, tho I like quizshows actually too. Ahh, who cares, keep going, but you might get an answer if you ask a question...

---

### Post by jokakid on 2008-09-25
```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...
ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.11.

./compiz-check: line 715: [: : integer expression expected
           [ OK ]
```

will this help

---

### Post by jokakid on 2008-09-25
well i work at dell so i guess ill just grab a new one :lolflag:

---

### Post by justsomedude on 2008-09-25
^^ Not a bad idea. Just did some research on your card, I don't think it's possible.

Good luck...

---

### Post by j.miller565 on 2008-09-25
same here found out that Compiz barely works on a GeForce 2 card so it definitely won't run on your RIVA TNT2 card sorry 

Good luck with getting a new one though, that's if you're planning to anyway.

PS. a nVidia GeForce FX 5200 works quite well with Compiz-Fusion plus it's a pretty cheap card. That's what I'm using right now, but I'd suggest something better than the 5200 since it does have a tendency to slowdown (a lot) when activating more graphically intensive modes in Compiz-Fusion. Hope that helps

---

### Post by loomsen on 2008-09-25
Tho, 64MB of RAM are enough to run compiz. I'd try and do what the error tells me, get a newer version of nv-control (1.6 out in the meanwhile)

Usually its like... the older the hardware is, the BETTER the support gets.

But it seems you are just running the wrong driver.

```

sudo apt-get remove --purge nvidia && sudo apt-get update && sudo apt-get install nvidia-glx-legacy 
```

should fix it. Or just open up synaptic to clean up anything currently installed by nvidia. Rightklick --> mark for complete removal.

Then do the steps above, just to make sure you won't get hung by obsolete/residual settings. Finally you should reconfigure your xorg.conf.


IN A ROOT TERMINAL(i forgot this aint possible with ubuntu, is it?), YOU SHOULDNT HAVE ANY SESSION RUNNING (To stop your current session, hit Ctrl+Alt+F2. Now you should drop to a terminal, asking you to login.Do so.)

Then do:
```
 sudo /etc/init.d/gdm stop
```
to stop gnome (kdm if you're running kde)
then the steps mentioned above, as I said, it should be fine if you remove your actual driver through synaptic, but to install the new you should stop your X server.

---

