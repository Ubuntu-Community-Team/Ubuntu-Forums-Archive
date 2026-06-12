---
title: "No sound since update."
date: 2015-11-19
forum: Hardware
---

### Post by Thomas_Soenen on 2015-11-19
Hello,

I can't use my sound card since yesterday.

I'm on Ubuntu 14.04 and the only things I did that could have done something yesterday was updating (and saddly I didn't pay that much attention to what I did update).

VolumeIcon doesn't show on tray anymore, alsamixer doesn't launch either.

But I tried some things, like things said on this page: [URL="https://help.ubuntu.com/community/SoundTroubleshooting"]https://help.ubuntu.com/community/SoundTroubleshooting
[/URL]
It seems that my sound cards are correctly installed:

> $ sudo lspci -v | grep -A7 -i "audio"
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
    Subsystem: Lenovo Device 2227
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f1130000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
--
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
    Subsystem: Lenovo Device 2227
    Flags: bus master, fast devsel, latency 32, IRQ 48
    Memory at f1134000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel



When I try the following command to play a sound nothing happens:
> [INDENT]$ aplay /usr/share/sounds/alsa/Front_Center.wav
Lecture WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Fréquence 48000 Hz, Mono
[/INDENT]


When I try to execute VolumeIcon I get this error:> [INDENT] $ volumeicon
Failed to create secure directory (/run/user/1000/pulse): Permission non accordée
volumeicon: alsa_backend.c :86 : asound_get_volume:  l'assertion « m_elem != ((void *)0) » a échoué.
[1]    14629 abort (core dumped)  volumeicon
[/INDENT]

When I try to execute pulseaudio -C I get this one:> [INDENT]pulseaudio -C
E: [pulseaudio] core-util.c: Failed to create secure directory (/run/user/1000/pulse): Permission non accordée
[/INDENT]

And when I try it with sudo:> [INDENT]$ sudo pulseaudio -C
W: [pulseaudio] main.c: Le programme n'est pas prévu pour être lancé en tant que root (sauf si --system est renseigné).
E: [pulseaudio] core-util.c: Home directory not accessible: Permission non accordée
[/INDENT]

I already tried reinstalling pulseaudio and alsa as well. I also tried reinstaller libasound2 and linux-sound-base.

I also used a command yesterday (can't remember which one) that told I was muted or not and my volume, all was 100% and muted was "no".

Can someone help me on this matter ? I'm running out of ideas :)

I searched on the web, and did find some people with the same issue but no fix...

thanks for your time !


EDIT:

I tried doing *sudo chmod -R thomas:thomas /run/user/1000/pulse *but I still get this error:

> $ volumeicon
volumeicon: alsa_backend.c :86 : asound_get_volume:  l'assertion « m_elem != ((void *)0) » a échoué.
[1]    14733 abort (core dumped)  volumeicon


---

### Post by pqwoerituytrueiwoq on 2015-11-19
maybe reinstalling pulseaudio and volumeicon will work
also try reseting your sound config
rm -rf ~/.config/pulse

---

### Post by Thomas_Soenen on 2015-11-19
Hello,

Thanks for your fast answer, I tried what you told me but no success.

Exactly the same error after I rebooted :s

Thanks anyway !



PS: I see you got a Fractal Design tower :D they're such beauties don't you think ?

I got an R3 at home, without the glass :p but I have a crossfire of 2 r9 290 inside with an AMD FX93xx and 16Gb :D (Fallout 4 love it, but only on windows D: )

Anyway, you should try the Caviar Black series, better perfs than blue one and not that much costly (1Tb was around 80&#8364; when I brought it).

---

### Post by Yellow Pasque on 2015-11-19
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Thomas_Soenen on 2015-11-19
Hello Temüjin,

[http://www.alsa-project.org/db/?f=455991408656ac2dbf031e4e1e535d3a0c72c5f4](http://www.alsa-project.org/db/?f=455991408656ac2dbf031e4e1e535d3a0c72c5f4)

Here's your link ^^

Thanks for your help,

---

### Post by Yellow Pasque on 2015-11-19
I'm a bit confused why your alsa lib/util versions are mismatched. Since you're running Trusty, the library version should be 1.0.27.2 as well. [https://launchpad.net/ubuntu/trusty/amd64/libasound2](https://launchpad.net/ubuntu/trusty/amd64/libasound2)
I don't know if that's causing the issue, but I find it suspicious.
```
Library version:    1.1.0
Utilities version:  1.0.27.2
```

See what output this gives:
```
apt-cache policy libasound2
```

Also, double-check that pulse is in the audio group:
```
cat /etc/group | grep aud
```

---

### Post by Thomas_Soenen on 2015-11-19
Yes that was it !

I compiled 1.1.0 so I could compile another tool.

Didn't think it would do this ... I compiled back 1.0.27.2 I downloaded from alsa website and now I have my sound back.

I'm really sorry, that was my fault, I'll keep this error in mind.

Thanks for your help and your time :)

---

### Post by pqwoerituytrueiwoq on 2015-11-19
> **Thomas_Soenen said:**
> 
PS: I see you got a Fractal Design tower :D they're such beauties don't you think ?

I got an R3 at home, without the glass :p but I have a crossfire of 2 r9 290 inside with an AMD FX93xx and 16Gb :D (Fallout 4 love it, but only on windows D: )

Anyway, you should try the Caviar Black series, better perfs than blue one and not that much costly (1Tb was around 80€ when I brought it).
yes, but i wish it was not so expensive (paid $80 for mine)
the only difference the blue/black is the warranty length, with the exception of 2.5" drives which is why i have a WD Black in my laptop
i just got a WD Blue 1tb for $45 it will be here Saturday (thought it might be here Friday based on the tracking data)
i should update that link and take some new pics, i have 16gb ram now and a PCIe NIC installed now

---

### Post by Thomas_Soenen on 2015-11-20
> **pqwoerituytrueiwoq said:**
> yes, but i wish it was not so expensive (paid $80 for mine)
the only difference the blue/black is the warranty length, with the exception of 2.5" drives which is why i have a WD Black in my laptop
i just got a WD Blue 1tb for $45 it will be here Saturday (thought it might be here Friday based on the tracking data)
i should update that link and take some new pics, i have 16gb ram now and a PCIe NIC installed now

Well I brought mine a year ago, maybe even more and it was much more heavily priced. Around 130€ if I remember correctly :s

Yeah well 1Tb blue for 45$ is a very good price, I which I could find such a price in europe xD

16Gb is definitly a good idea right now, ram doesn't cost much and it give you space :)

---

### Post by pqwoerituytrueiwoq on 2015-11-20
i only buy stuff when it is on sale, standard sale price for a R4 is 80, i saw 75 once
i had to order 2 HDDs to get that price, but only 1 is for me the other is for a client (typical sale price is 48 right now)
i picked up my last 4gb for ~17.5 (used), another 8GB cost me 40 (back when DDR3 was cheap) and my 1st 4GB cost me 40 (back in ~2011)
i use my RAM for a ram disk (nobody has time for a HDD's I/O) and virtualboxes

---

