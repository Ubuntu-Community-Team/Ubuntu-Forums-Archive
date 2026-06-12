---
title: "Karmic - Toshiba P105, no sound after suspend"
date: 2009-11-03
forum: Hardware
---

### Post by Aroenai on 2009-11-03
Hi,
Ok, so my laptop is a Toshiba Satellite P105-S9722 and trying to run Ubuntu on it has been a pain since when I started with 8.10, luckily I've got most of the issues fixed with 9.10 and installing the omnibook svn (why isn't this included in Ubuntu??). The only issue left is that the sound completely dies after resuming from suspend. No sound from the speakers, or the headphone jack but everything works fine if you restart the system.

These are all the names I know for my soundcard:
Intel HDA
Conexant Waikiki
Conexant CX20551
5047 (Waikiki)

Installing the linux-backports-alsa-karmic-generic package didn't help, does anyone know of a solution to this? I'm running Ubuntu 9.10 x86_64.

---

### Post by Aroenai on 2009-11-04
Anyone?

---

### Post by nystire on 2009-11-13
I have the same problem on a Toshiba P105-S9337. The sound card in this laptop is a Conexant CX20549 (Venice).

---

### Post by Anarci on 2009-11-13
Does running 
```
pulseaudio -k
pulseaudio & 
```help?

---

### Post by Aroenai on 2009-11-13
no, killing pulseaudio, restarting the alsa module, or even setting the model in alsa-conf all do nothing.

---

### Post by mkw87 on 2010-06-06
Did anyone ever find a solution to this?  I am having the same issue on a P105-S6084.

---

### Post by erenay on 2010-12-28
Hi, I have the same problem with Toshiba P100 with all versions of Ubuntu, and couldn't find a solution yet.

---

### Post by mkw87 on 2010-12-28
> **erenay said:**
> Hi, I have the same problem with Toshiba P100 with all versions of Ubuntu, and couldn't find a solution yet.

Still no solution - bug filed [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/590502").

---

