---
title: "can't enable effects, Drivers?"
date: 2008-07-17
forum: General Help
---

### Post by vancedus on 2008-07-17
Hi,  I am very new to Linux and I'm running 8.04.  I first encountered a problem when trying to enable the visual effects, I was told that they couldn't be enabled.  I am running a Geforce 8400 256 Mb.  when I go to "Hardware drivers" none show up to be enabled.  I then reinstalled nvidia-glx-new with synaptic.  I have tried quite a bit of forum stuff but nothing seems to help.  When I try to go to my nvidia settings it tell me that I don't have a NVIDIA x Driver.  Also, going into NVIDIA xconfig doesn't take me to anything.  If you have any advice please help.  Thank you

P.S. Yesterday I logged on and i could only see things in 640x480, related?  I am currently telling my system I have a large monitor so I can still get 1280x800 but it won't auto detect the correct resolution.

---

### Post by darco on 2008-07-17
Open a terminal.....type compiz , hit enter and post the results in this forum
darco

---

### Post by Cl0ud9 on 2008-07-17
Try using envyng to install the driver.
```

sudo apt-get install envyng-core
sudo envyng

```

---

### Post by vancedus on 2008-07-18
hey,  Thanks a lot. going into envy from the terminal worked perfectly.  I had tried it through synaptic and got nothing before. thankyou.

---

