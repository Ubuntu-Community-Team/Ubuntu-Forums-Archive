---
title: "Intrepid Ibex (8.10) on HP NC6120"
date: 2008-11-07
forum: Hardware
---

### Post by mariourk on 2008-11-07
I have installed Ubuntu 8.10 (Intrepid Ibex) on my HP NC6120 laptop. Most things work without any problem. However, the special keys won't work. For example, the special FN-keys, the wifi-key and the keys to alter (or mute) the sound.

Does anybody know how to fix this?

Thanks! :)

---

### Post by carens on 2008-11-07
**FN-Keys**
I would like to know too...

**Wifi-key**
Works on my HP, but had to add "/etc/modprobe.d/ipw2200" file with entry "options ipw2200 led=1" to get the actual light working.

**Mute-key**
Works on my HP, but had to add to "/etc/modprobe.d/options" file "options snd-intel8x0 ac97_quirk=7" to get the actual light working. You have to check your sound hardware for the right option.

---

### Post by mariourk on 2008-11-07
You're right. The wifi-key and the volume-keys do work, although the led on them does not. Not very smart of me to blindly assume they wouldn't work :oops:

That leaves the Fn-keys. Anyone? :-k

---

