---
title: "USB Sound Card Power On Command"
date: 2015-03-26
forum: Hardware
---

### Post by AlexDraper on 2015-03-26
Hi there,

I'm hoping someone will be please able to help me with a problem I've been having with my USB sound card (a Logitech Z-Cinema). Normally you power on the device with it's remote, but the remote just died in a tragic battery explosion. Under Windows you can use the official software to power on the device from a utility, however neither Amixer nor Pacmd expose that control to me. At the moment the device is off and I'm not sure how to ask it to switch on again. Does anyone know how to fix this?

Thanks

---

### Post by AlexDraper on 2015-03-27
Bump

---

### Post by Rob Sayer on 2015-03-27
A quick search indicated it's a speaker system with USB input from a few years ago.  Sound right?

Unfortunately it also found a comment from a logitech employee saying they don't actually support linux.  I wish this was less of a surprise to linux noobs.  For something like this it means the basic functions may work but the added features quite often don't.

You could try installing Wine and running the windows setup utility with that.

---

### Post by AlexDraper on 2015-03-27
That's the one Rob. I read the same comment, so I know official support is out, what I was hoping for is a more general command line method of asking the speaker to wake up. For example the official program can adjust bass levels too, but you don't need it for that, you can use alsa.

---

