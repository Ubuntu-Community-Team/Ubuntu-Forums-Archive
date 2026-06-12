---
title: "Ubuntu 8.10 on HP 6730s"
date: 2009-02-06
forum: Hardware
---

### Post by IdmRek on 2009-02-06
Runs perfect. 
I love it, purple colour scheme is neat. Wireless and Sound works perfect.
I removed vista from this, and dualbooted Xp sp3 with ubuntu. Makes a tidy laptop :D

---

### Post by Kleinpetri on 2009-02-23
Hi,

thanks for writing this little post which made my decision very easy. ;)

Greetings,
Petrie

---

### Post by aknaton on 2009-04-04
> **IdmRek said:**
> Runs perfect. 
I love it, purple colour scheme is neat. Wireless and Sound works perfect.
I removed vista from this, and dualbooted Xp sp3 with ubuntu. Makes a tidy laptop :D

I also have a HP 6730s. But I dont get the wireless or the sound to work. I first run 8.10. But I upgraded to 9.04 in hope to get them to work. But no such hopes. Any advice how to proceed?

/aknaton

---

### Post by aknaton on 2009-04-11
Now everything (I hope) is working.

The wireless thing was due to that I had pressed the wrong button on the computer (and turning it off) :oops:.

In an attempt to fix the sound I upgraded to 9.04 beta. No such luck. So I trawled the net and found this solution:

In the file [FONT="Courier New"]/etc/modprobe.d/alsa-base.conf[/FONT] (the name of this file may differ in the different versions of Ubuntu) I added the line:

[FONT="Courier New"]options snd-hda-intel model=laptop[/FONT]

at the end of the file (you must sudo to change it). It works like a charm :guitar:

---

