---
title: "No sound on ancient machine"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by rinseout on 2005-07-31
Hi;

I've spent the last day or so putting Ubuntu on an ancient Win98 box that had one too many viruses. Everything seems to be working but sound... ls /dev/dsp* doesn't list any matches, and lspci doesn't show anything suggestive of a sound card. But I know the system has sound, because it was used a bit for streaming radio in its win98 days.

How can I get the sound going? I have no idea what kind of sound card the thing has; only that this is one of these ancient PII 120Mhz 64 Meg boxes that everybody has lying around. The BIOS is about 1996-era.

---

### Post by rinseout on 2005-07-31
Just as a followup to this, I have taken a look at the back of the machine and it looks like the device actually is a card (occupying a slot); it has (in order from left to right):

something like a joystick port (bigger than a 9-pin serial port, smaller than a parallel port)
a line out (speakers are plugged in)
a volume control
and two other audio jacks (line in and mic in, maybe?)

Hopefully this will help narrow down what I need to do.

---

### Post by heimo on 2005-07-31
This could help:
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

Your card is probably ISA-bus. Identifying it is essential to get it working. You could try to install isapnptools and run pnpdump to get some hints (I'm not sure about this, but I remember doing something like that when I had computer from that era).

---

