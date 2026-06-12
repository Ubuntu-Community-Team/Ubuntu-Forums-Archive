---
title: "sound working...but no /dev/audio ??"
date: 2010-12-02
forum: Hardware
---

### Post by welshchap on 2010-12-02
Hi All,

just upgraded to maverick from 10.04 and generally looking good 

One issue is sound related . 

although my sound is working,  I no longer have a /dev/audio

I presume this is as a result of pulseaudio ?

the command line package I'm trying to use does have -i and -o  options to specify another device file although it defaults to /dev/audio

in  /dev/snd I have :

```

/dev/snd$ ls
by-path  controlC0  hwC0D3  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer
welshchap@marconi:/dev/snd$ cd by-path
welshchap@marconi:/dev/snd/by-path$ ls
pci-0000:00:14.2

```

 I presume that I need to specify one of these devices ? (e.g. -i =/dev/pcm****) but how do I find which one please ?

Alternatively how do I get /dev/audio back please ?

sound driver from sudo lspci -v is :

```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Foxconn International, Inc. Device 0e0c
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at facf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

many thanks in advance 

cheers

Welshchap

---

### Post by gewone on 2010-12-27
Yeah. Like TS mentions, it's messy.
Some apps want /dev/ specification, eg. gtkrecordmyscreen.
What to symlink where to make it work?

---

### Post by celiapgt on 2011-03-21
Indeed this happens. I have the same problem. I want to use vlc to capture video from my webcam and I don't know which device should I use.

---

### Post by kappel79x64 on 2011-03-21
[http://alsa.opensrc.org/ALSA_device_labels](http://alsa.opensrc.org/ALSA_device_labels)

here to find out about the pcm devices

hope it will help you a bit ;)

---

