---
title: "Lost audio trying to install most recent alsa drivers"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by qiemem on 2006-11-27
I have a Dell Inspiron 9300 running Edgy, been running Ubuntu for over a year now.

Recently, I had to update my alsa drivers to work with a microphone I recently purchased. So I followed Fraz's comment on [this thread]("http://ubuntuforums.org/showthread.php?t=272166"), successfully (sort of) installing alsa-drivers-1.0.13. Since then I have had no audio whatsoever; I added "snd-hda-intel" to /etc/modules and everything. In trying to fix this, I've been working off of LordRaiden's amazing [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa+drivers") but to no avail. Here's what I've been getting:
```

$ aplay -l
aplay: device_list:222: no soundcards found...

```
and from "lspci -v", I find:
```

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 0189
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ed00 [size=256]
        I/O ports at ec40 [size=64]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```
which I'm assuming is my soundcard.

At first I tried removing (with --purge) and reinstalling all alsa stuff in accordance with LordRaiden's guide, but this didn't change anything.
I then tried compiling the alsa drivers from the source in the repositories, to the same result. Finally, I tried again installing the drivers from alsa-project.org, but this time following LordRaiden's instructions (installing alsa-driver-1.0.12rc2 instead). None of these produced any significant errors, all seemed successful, but none of them got my sound back. 

I then checked my BIOS to see if I did actually have the soundcard I thought I did, and it said Sigmatel something (I forgot to write down the number: I'll get it again if its important). Did I screw up? I thought I had intel card, but I guess I could've been wrong. I don't remember what the lspci -v said before I tried compiling those first drivers. But I couldn't find anything about sigmatel on the alsa-project website.

Anyway, anyone know what I'm doing wrong? Help would be greatly appreciated. I'm missing my music pretty badly :(

---

### Post by qiemem on 2006-11-28
Someones gotta know something about this. Alsa experts? Anyone?

---

### Post by greybirds on 2006-12-01
No answers for you, but I have the same problem and am working on it. If I find anything, I'll let you know.

---

### Post by qiemem on 2006-12-01
Nice to know that I'm not alone on this one, though I'm sorry to hear you're in the same boat. Looking forward to hearing what you figure out! And of course I'll keep ya posted if I find anything.

I tried booting from a live cd today (though I did it to diagnose another problem) and my sound was working fine. While this doesn't tell me much, at least I know its not a hardware problem, but most likely a problem with my installation of alsa.

If anyone can offer any advice on this, I would be very grateful. Even just places to look for information, or guesses. I'm really pretty stumped on this one.

---

### Post by zetaz7680 on 2007-04-01
Same problem here just today trying the 1.0.14rc3 ALSA.

---

