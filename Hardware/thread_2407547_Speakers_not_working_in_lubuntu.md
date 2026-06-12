---
title: "Speakers not working in lubuntu"
date: 2018-12-05
forum: Hardware
---

### Post by kevin202 on 2018-12-05
Hi guys, i need your help.

I've recently bought a new notebook, this one is not pretty good, so i solved to install lubuntu (I used lubuntu in another notebook before,16.04, and 18.04).
I installed lubuntu 18.10 and is georgious, i love it. But i have a problem with my audio, after removing windows 10 the speakers are not working (sound is working with headphones). After that, i did a lot of strange things, then now i cant configure sound in bottom desktop bar, but i do it by writting pavucontrol in console. Can please someone help me?

Also i have to say that my notebook have a touchscreen and is not working too, but i don't care.

Sorry if a had any redacting fail. Thank you.

---

### Post by Frogs Hair on 2018-12-06
Try the following.

```
[COLOR=#000000][FONT=&quot] [SIZE=2]sudo alsa force-reload[/SIZE][/FONT][/COLOR]
```

---

### Post by kevin202 on 2018-12-06
done, still same :/

---

### Post by Frogs Hair on 2018-12-07
Can you explain?>  [COLOR=#000000]i did a lot of strange things,[/COLOR]

---

### Post by kevin202 on 2018-12-09
I've re-installed lubuntu, so it does not matter now, it's pretty normal, but speakers still not working. :c. Any idea? Ty for your answers buddy

---

### Post by Frogs Hair on 2018-12-10
Here are two commands , the first will identify your audio device and the second will display mixer levels in the terminal. 

```
lspci 
``` ```
alsamixer
```


Moved to *Hardware*

---

### Post by Yellow Pasque on 2018-12-10
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by kevin202 on 2018-12-12
lspci
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)


Alsa info

ww.alsa-project.org/db/?f=67f321a375ab85b46fd4f07edab2b1638d3c0dd3

(When i used alsa info i got this in term, cat: '/sys/module/snd_soc_sst_bytcr_rt5651/parameters/*': No such file or directory)

Alsamixer:

[https://pasteboard.co/HRoPLJn.png](https://pasteboard.co/HRoPLJn.png)

---

### Post by Frogs Hair on 2018-12-12
Do you have a speaker on/off button on the note book as I do and did you check its status.

---

### Post by kevin202 on 2018-12-16
Nope, i have not any button.

---

