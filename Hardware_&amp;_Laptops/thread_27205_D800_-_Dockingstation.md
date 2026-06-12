---
title: "D800 - Dockingstation"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by NorLan on 2005-04-15
Hi

as this is my first post in this board i would sent my big thanks to the hard working developers and other guys out there which make such a great distr (also the deb's in here *gg).

so to my problem i use a Dell Latitude D800 with dockingstation but i have a lille problem with the sound. sound is ok over laptop speaker and the headphone output is also ok - but over the dockingstation i get no or a very "glitchy" output. does anybody has the same probs with the docking ?

affected hardware:
Dell D800 1,7
D/Port

---

### Post by NorLan on 2005-09-04
got a fix for it

change the samplingrate

first -> search for the numid of "IEC-default"
amixer controls

second -> 35 was my numid for iec-default and the 6 at the end sets samplingrate to 96kHz
amixer -c 0 cset numid=35 6

---

### Post by NorLan on 2005-09-08
hmm
problem again - as in reply 1 i fixed the problem with the "amixer -c 0 ....

but this is a fix which lasts for a few moments -- after half an hour it falls back to silence typing this into the shell brings sound back again .... where is the adequat config entry to make this resitant ?




some alsa debug for those who can give a better suggestion:

```
ALSA Audio Debug v0.0.9 - Don Sep  8 20:05:46 CEST 2005
http://alsa.opensrc.org/?page=aadebug

Kernel ----------------------------------------------------
Linux hugo 2.6.12-8-386 #1 Tue Aug 30 22:41:30 BST 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           30016  3
snd_ac97_codec         71804  1 snd_intel8x0
snd_pcm_oss            46368  1
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with STAC9750,51 at 0xf4fff800, irq 5
 20: [0- 4]: digital audio playback
 27: [0- 3]: digital audio capture
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: Datei oder Verzeichnis nicht gefunden
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2c  pcmC0D3c  pcmC0D4p  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) M processor 1.70GHz
cpu MHz         : 599.559

RAM -------------------------------------------------------
MemTotal:       516228 kB
SwapTotal:     3421836 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

---

### Post by salvatore on 2005-09-16
Im experiencing this exact issue.  Has there been progress towards a resolution?  My Googling hasnt revealed anything yet.

---

### Post by NorLan on 2006-04-12
i did a lille progress after my last posts (forgottn to update here)

```

     amixer controls                     %% search the id of IEC-default
     amixer -c 0 cset numid=35 6   %% 35 is IEC-default 6 = 96kHz

```

this fixes the problem for a unknown number of minutes/hours

mfg

---

