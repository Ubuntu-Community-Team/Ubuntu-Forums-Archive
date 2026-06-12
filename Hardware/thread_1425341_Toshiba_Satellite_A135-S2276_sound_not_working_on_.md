---
title: "Toshiba Satellite A135-S2276 sound not working on Ubuntu 9.10"
date: 2010-03-08
forum: Hardware
---

### Post by Marc Di Pinto on 2010-03-08
I just installed(fresh) Ubuntu 9.10 on this Toshiba laptop(satellite A135-S2276) and the sound doesn't work. It doesn't work on the speakers nor the headphones. The Sound shows "Dummy Output" and nothing else.

I'm not an expert in computer, and I'm new to Linux.

Anyone knows something to make the sound work?

---

### Post by d3v1150m471c on 2010-03-08
System > administration > hardware drivers. check and see if you have the drivers for everything.
next:
```

alsamixer

```
try adjusting your levels and see if that helps.

---

### Post by Marc Di Pinto on 2010-03-09
Hard Drivers says No proprietary drivers are in use on this system. and nothing else.

In the Terminal using alsamixer says No mixer elems found.

I did update it just 30 minutes ago.

---

### Post by Marc Di Pinto on 2010-03-09
anyone have any idea of what to do to get it to work?

---

### Post by Marc Di Pinto on 2010-03-09
It seems that it's working now.
sudo apt-get install linux-backports-modules-alsa-karmic-generic
I did this on the terminal and restarted it.

---

