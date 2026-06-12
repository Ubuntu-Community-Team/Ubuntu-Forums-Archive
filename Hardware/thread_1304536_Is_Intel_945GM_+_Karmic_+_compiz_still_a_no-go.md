---
title: "Is Intel 945GM + Karmic + compiz still a no-go?"
date: 2009-10-29
forum: Hardware
---

### Post by Daimoneze on 2009-10-29
I've known about the kernel issues with the newer Intel drivers, and that we were waiting for the release of Karmic before adopting the newer kernel, but is the issue still there? I tried searching around a bit but info seems to drop off sometime after Alpha 2. Makes me think I'm having an isolated problem.

---

### Post by mfarley on 2009-10-30
I can't get it to work with a fresh 9.10 install either (945BM).. It's not just you :(

---

### Post by mfarley on 2009-10-30
Actually, I just fixed it by running: ```
sudo apt-get install x11-utils
```

---

### Post by Varda on 2009-10-30
I have the same problem with the Acer Aspire One AO751h Intel GMA500 :S

//edit: I tried 
sudo apt-get install x11-utils
But there was a message error about xll-utils not found =/

---

### Post by mfarley on 2009-10-30
> **Varda said:**
> I have the same problem with the Acer Aspire One AO751h Intel GMA500 :S

//edit: I tried 
sudo apt-get install x11-utils
But there was a message error about xll-utils not found =/

Make sure you typed "x11" x-one-one, not x-el-el:

sudo apt-get install x11-utils

The package should exist, see: [http://packages.ubuntu.com/karmic/x11-utils](http://packages.ubuntu.com/karmic/x11-utils)

---

### Post by mannheim_68161 on 2010-01-15
i'm running ubuntu 9.10 on a FujitsuSiemens (AMILO Pro), that also uses a 945GM-chip. one og the problems i encounter is that hooking up my tv-set leads to system-crashes and weird display-malfunctions.

can anybody help?

---

