---
title: "Ubuntu on Toshiba A200-1SX"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by kurotenshi on 2008-01-12
I've installed Ubuntu 7.10 on my new Toshiba A200-1SX. I've managed to put the graphics driver to work and the Atheros wifi card works to with madwifi. But now I have two problems:

1 - The wifi card works but if I shut down the computer when I enter Ubuntu the card isn't detected again, then I have to go to the drivers folder, do the make install and reboot, and it's working again.

2 - the sound card (or cards) was detected as being realtek ALC268 and HD intel (windows does recognize the two also) the sound was working for the speakers but the headphones jack were not and they did not silenced the speakers. Wile trying to solve this I managed to make the two unrecognizable and now they appear in the mixer but i have no sound at all.

In addiction to these two problems i'd like to know if there is a way to have support for the new toshiba multifunction touchpad and the rest of the multimedia buttons.

Also do I have to tweek anything from the Ubuntu 7.10 generic x86 kernel to improve dual core support?

EDIT#1 - The sound is partially OK, thanks to Knorr and ilkkal on [http://ubuntuforums.org/showthread.php?t=551615&highlight=realtek+alc268]("http://ubuntuforums.org/showthread.php?t=551615&highlight=realtek+alc268"). Now I have sound on the headphones and the speakers at the same time. I have to silence the speakers with the "FRONT" slider in the alsa mixer

---

### Post by Michalxo on 2008-02-29
Hello, maybe I can point you to  another pages to solve your problems,

1, I am not experienced user and I have a200-1gs, intel 4965 wifi, and sometimes it dont work for me either. So i had make wifireboot alias (sudo 3x rmmod {drivers}, and modprobe {these 3 drivers again})
and it works :) sometimes when wifi gone dead I just sudo ifup / ifdown wlan0 :)  And it works flawlessy :)

2, try this page [http://ubuntuforums.org/showthread.php?t=568463&page=5](http://ubuntuforums.org/showthread.php?t=568463&page=5) it helped me to solve the "jack problem" :)  just add few lines to one file (read forum) and that's all.

Dualpad (touchpad) isnt working for me too in ubuntu :(  In win it runs nicely (nice blue light :) )
Maybe someone will help us with this problem.

---

