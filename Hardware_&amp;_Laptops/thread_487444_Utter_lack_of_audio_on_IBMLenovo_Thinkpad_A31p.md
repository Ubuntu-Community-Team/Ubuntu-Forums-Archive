---
title: "Utter lack of audio on IBM?Lenovo Thinkpad A31p"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by Gideon Stargrave on 2007-06-29
I recently installed Feisty on my laptop. Before it was running XP and had no issues with sound, so I know the hardware works. According to lspci the audio device is an Intel Corporation 82801CA/CAM AC'97 Audio Controller. As far as I can tell the drivers and stuff are detected and it should work, but nothing comes out of the speakers. I did some messing around with the levels in alsa but it didn't do anything. I haven't the foggiest idea what else to try x.x This is the only problem I'm having right now and it sucks, because I almost always have music playing when I'm working.

---

### Post by ugm6hr on 2007-06-29
Did you try **unmuting** and maximising all volumes in alsamixer?  That works on some laptops (where the speakers are "surround").

---

### Post by Gideon Stargrave on 2007-06-29
I did. Still nothing. :[

---

### Post by bwhat on 2007-07-06
I experienced this problem on my a31p - i used the BIOS'  "load default config", rebooted and voilá, the drums on the start of GDM greeted my ears...

---

### Post by Gideon Stargrave on 2007-07-06
That did it, the audio's very clippy but it exists - thanks!

---

### Post by Gideon Stargrave on 2007-07-07
Well, crap. Rebooted and now there's no more sound, even if I reset the bios again.

---

### Post by obiman03 on 2007-10-01
i had the same problem but when i loaded the default setting it was worse, it stopped booting into windows, always coming up with a blue screen and restarting

---

