---
title: "System Beep Broken"
date: 2008-11-01
forum: Hardware
---

### Post by fuzzypig on 2008-11-01
I have a Compaq Presario C762NR Laptop with a Conexant soundcard.

Ever since I first installed Ubuntu on this laptop, the system beep has sounded more like a system "pff", with fuzz and static in the sound. It doesn't sound that way on other computers. I've gone through several distribution upgrades, but it always sounds the same. Any ideas?

```
fuzzypig@fp-paraphymn-ubuntu:/proc/asound/card0$ grep "Codec" /proc/asound/card0/codec#0
Codec: Conexant CX20561 (Hermosa)
```

```
fuzzypig@fp-paraphymn-ubuntu:/proc/asound/card0$ sudo lspci | grep "Audio device"
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by phidia on 2008-11-01
If by the system beep you mean the post test sound when you first power up-that has nothing to do with  the OS installed. Either the speaker itself is damaged or maybe there's a bad connection.

---

### Post by fuzzypig on 2008-11-01
All other sound is fine.

I'm talking about the beep that happens when I press backspace one too many times on the command line. Is this a problem with the hardware?

---

