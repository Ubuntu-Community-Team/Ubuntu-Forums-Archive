---
title: "More Sound Problems"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by rgovostes on 2005-08-21
I followed the guide posted here and got my sound to work. Thanks!

However, I just ran the update installer and part of the updated software was the linux kernel or something (I'm not sure, but I can't seem to find a log of the software updated). Now when I start up or shut down, it seems to be trying to run a program with arguments it doesn't understand, which results in several beeps. When the computer is started up, it doesn't recognize my sound card anymore.

Update: The program being called seems to be "amixer"

Any idea what's up?

---

### Post by rgovostes on 2005-08-24
Performing "sudo /etc/init.d/alsa restart" reproduces this lovely beeping symphony so that I can actually see what it's doing. It's beeping because it's being passed an "invalid card number." After thoroughly annoying me, I get this message:

> /etc/init.d/alsa: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1267: No soundcards found...'. [ ok ]

No advice?

-- Edit -- I figured it out, argh, I suck at life.

---

### Post by oofnik on 2005-08-25
Just saw that you figured it out, mind helping me out as well? Thanks! :)

---

### Post by rgovostes on 2005-08-25
If you already followed the advice in [this topic](http://ubuntuforums.org/showthread.php?t=21211), you can do it again simply with:

cd /usr/src/alsa-driver-1.0.8
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo make
sudo make install

... and reboot. It only takes a second to do over again and fixes the problem. You'll notice you only get like one beep when shutting the machine down, and on its way back on you should be golden.

---

