---
title: "No sound..."
date: 2009-04-15
forum: Hardware
---

### Post by Apache0c on 2009-04-15
Hello, this is my first post so I should start out by saying hi and that I'm thankful for the help of this community.

I'm running Linux Mint 5 LTS which is based on Ubuntu 8.04 LTS I believe. I posted my question in the Linux Mint forum but it's a small community, I havent really seen anyone actually providing help over there.

So I'm hoping that someone here can help me since we are all part of the same Open Source/GNU/Linux/Debian family. 

I've been toying with Linux for many years and when I say toying for many years I actually mean that I just learned what sudo is last night. I'm a total noob, just want to get that out in the open. But I have a deep love for Linux and Open Source and a willingness to learn, so any patience with me that you can afford will be much appreciated. 

I'm going through the troubleshooting guide at help.ubuntu.com/community/SoundTroubleshooting and this is the info that I've pulled up. 

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


There doesnt appear to be any alsa kernel modules listed here like there was in the guide.

lspci -v | less
```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Gateway 2000 Unknown device 0215
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Gateway 2000 Unknown device 0215
        Flags: medium devsel, IRQ 18
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: [50] Power Management version 2

```

If nobody has a a fix, maybe someone could help me reinstall the ALSA sound module and/or sound drivers.

---

### Post by khelben1979 on 2009-04-15
If you intend to reinstall ALSA, then I suggest that you look in [this thread]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script").

The way I did this kind of reinstallation was that I downloaded all the source tar balls from [the Alsa Project homepage]("http://www.alsa-project.org/main/index.php/Main_Page") and compiled up all the source, installed the source and then ran the ALSA upgrade script. I have been writing about this before in an old thread which I can take up to the surface if it's needed.

---

