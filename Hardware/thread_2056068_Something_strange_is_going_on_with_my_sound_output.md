---
title: "Something strange is going on with my sound output"
date: 2012-09-10
forum: Hardware
---

### Post by aria1121 on 2012-09-10
Hello all,
This is my second thread and I haven't used Linux for quite a while. But since my laptop denies to get Windows installed due to factory settings, I had to install Linux.
The strange thing is, while I was installing Xubuntu (live mode from USB), I was able to use headphones and built-in speakers. But after install (boot from hdd) and since then, I can't anymore. Weird, isn't it? So I searched all over the place about ALSA and reconfiguring and initialising stuff but nothing helped. FYI, here is the output of lspci about my audio configs:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Santa Cruz Operation Device 1043
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: oss_hdaudio

```So does anyone know how I can output sound regular again? Neither my headphone jack and built-in speakers are listed in the volume thingy. There is only a "dummy-output" available.

---

### Post by aria1121 on 2012-09-11
I have tried all the possible solutions that were mentioned on the forum but still nothing helped. Can anyone please help?

---

### Post by aria1121 on 2012-09-12
Isn't there a way to reset the sound settings? It is now three days I have no sound.

---

### Post by aria1121 on 2012-09-12
I just found it out myself. [Here]("https://www.youtube.com/watch?v=hG23OOayatI") is the vid providing the answer (steps described below).

[SIZE=3]**SOLUTION:**
[SIZE=2]
1. Open Terminal
2. Type in [COLOR=Lime][COLOR=Blue]aptitude[/COLOR][COLOR=Black] and press [Enter] ==> if it says it doesn't know what aptitude is, open Synaptic and install it. If aptitude does start, close Terminal and start it again, continue with step 3
3. Enter the following (as one line): [COLOR=Lime][COLOR=Blue]sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils  linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2[/COLOR]
[COLOR=Black]4. A message will appear saying you have to reboot your system, do so

And it should work. If it doesn't, check this out:
[https://help.ubuntu.com/community/SoundTroubleshootingGuide](https://help.ubuntu.com/community/SoundTroubleshootingGuide)
[/COLOR] [/COLOR][/COLOR][/COLOR][/SIZE][/SIZE]

---

