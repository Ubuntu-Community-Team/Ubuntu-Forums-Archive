---
title: "No Sound on Laptop running Jaunty"
date: 2009-07-29
forum: Hardware
---

### Post by JTmas on 2009-07-29
Greetings again folks,

I've been running fine on Ubuntu for the past few days, but just of late tried to play a sound through the inbuilt speakers on my Laptop. Long story short, no sound on either the laptop speakers, or through a headset or external speakers.

I've checked to the limit of my Ubuntu knowledge, which is checking if the volume was muted, it isn't.

So, Toshiba Satellite Laptop running Jaunty, no sound, and not a clue on how to go about getting it back.

Anyone have any ideas?

---

### Post by ZaHACKieL on 2009-07-29
Have you tried the sound in Windows or another OS, just to verify is not a hardware issue

---

### Post by JTmas on 2009-07-30
I have indeed. I used to use the speakers all the time when XP was installed, but quite a few issues forced me to change....

---

### Post by ZaHACKieL on 2009-07-30
Maybe try reinstalling the ALSA stuff. Let me know what happens

---

### Post by jroc777 on 2009-07-30
I have same issue on HP Pro book. dual boot Vista and sound works under windows.
No level bar in alsa for front speakers.

---

### Post by lswb on 2009-07-30
This works for me when sound fails on my 9.04 system. Open a terminal and try these commands:
```

rm .pulse-cookie
rm -r .pulse

```

If anyone knows why this works please share!

---

