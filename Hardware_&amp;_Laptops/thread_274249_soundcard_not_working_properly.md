---
title: "soundcard not working properly"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by Sander51 on 2006-10-09
Hi all,

I'm using ubuntu 6.10 Edgy Eft and I'm having a problem with my C-Media CM6501 soundcard (I also had the problem with Dapper Drake).

Esd works fine for me, but if I set in Mplayer/VLC the sound output to ALSA, or OSS, the sound is very high and fast, or it's just quiet. Some games don't start because of this sound problem. The games that start, don't have sound.

In Preferences => Sound there are two soundcards available: "MPU-401 UART" and "PNP Audio Device". I have only one soundcard though. I've set all the default Sound Playbacks to ESD.

Can someone please help me?
Thanks!

Sander(51)

---

### Post by Urreality on 2006-10-09
If you haven't already check out this post it worked for me when nothing else did.[URL="http://www.ubuntuforums.org/showthread.php?t=205449"]
http://www.ubuntuforums.org/showthread.php?t=205449[/URL]
Good Luck.

---

### Post by NAR on 2007-10-06
I have a similar sound card on my motherboard, lsusb shows this:
```

nar@narpc:~$ lsusb
Bus 002 Device 004: ID 0d8c:0201 C-Media Electronics, Inc. 

```

aplay also shows the device:
```

nar@narpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The problem is that alsamixer doesn't see this card:
```

nar@narpc:~$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such device

```

Is it possible that a device node is missing from /dev?
```

nar@narpc:~$ ls -l /dev/snd
összesen 0
crw-rw---- 1 root audio 116, 6 2007-10-06 15:32 controlC1
crw-rw---- 1 root audio 116, 5 2007-10-06 15:32 pcmC1D0c
crw-rw---- 1 root audio 116, 4 2007-10-06 15:32 pcmC1D0p
crw-rw---- 1 root audio 116, 3 2007-10-06 15:32 seq
crw-rw---- 1 root audio 116, 2 2007-10-06 15:32 timer

```

According to strace, alsamixer tries to open /dev/snd/controlC0. By the way, I'm using Feisty.

---

### Post by NAR on 2007-10-07
Putting the following into ~/.asoundrc solved the problem:
```

pcm.!default { 
type hw 
card 1 
} 
ctl.!default { 
type hw 
card 1 
}

```

---

