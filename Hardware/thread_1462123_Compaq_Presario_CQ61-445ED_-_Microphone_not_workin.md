---
title: "Compaq Presario CQ61-445ED - Microphone not working and Webcam is choppy"
date: 2010-04-25
forum: Hardware
---

### Post by gonzalioz on 2010-04-25
Hi all,

I just bought a [Compaq Presario CQ61-445ED]("http://h10010.www1.hp.com/wwpc/nl/nl/ho/WF06b/321957-321957-3329742-89318-89318-4074240-4115720.html") two days ago and immediately installed Ubuntu on it. Everything is working fine except the microphone and the webcam. The microphone doesn't work with the Sound Recorder and Skype. The webcam does work in Skype but it's extremely choppy.

I haven't been able to find anything on the internet about this. So I am hoping someone can help me. I am still a novice with ubuntu, so please tell me what information you need and I'll post it.

Thanks in advance!

ps: To get the sound working I added these lines to "/etc/modprobe.d/alsa-base.conf":

```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1 
```

I didn't change anything else.

---

### Post by lidex on 2010-04-25
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by gonzalioz on 2010-04-27
Thanks for your reply. This is the output:

```

taco@taco-laptop:~$ uname -a
Linux taco-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

taco@taco-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

taco@taco-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

taco@taco-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B2X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
taco@taco-laptop:~$ 


```

---

### Post by lidex on 2010-04-27
You should either upgrade alsa or install the alsa backports.
Backports:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

alsa-upgrade-script link is in my sig

---

