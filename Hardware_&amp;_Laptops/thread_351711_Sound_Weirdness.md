---
title: "Sound Weirdness"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by Plagued on 2007-02-02
Hello all,
  I have an interesting issue that I initially posted on the Kubuntu forums, but since I don't think it is necessarily KDE related, I thought I would post it here to see if anyone had any ideas.

The original posting on the kubuntuforums is [here]("http://kubuntuforums.net/forums/index.php?topic=13328.0").

Here is a copy of what I posted:

> Hello all,
  I have run kubuntu for a while, and finally decided that it was time to install it on my main computer @ work. What I am seeing is kind of weird. When I reboot the computer, the sound seems to work for a random amount of time. I use Amarok for a music player. I have tried other players, and they all are showing the same results (even mpg123, which is making me thing that it is probably not a KDE vs Gnome thing). The only way that I can consistently keep the sound working is to reboot whenever it dies.

  Here is some info on this box:

```
~$ uname -a
Linux kirk-G4 2.6.17-10-powerpc-smp #2 SMP Tue Dec 5 22:01:26 UTC 2006 ppc GNU/Linux

```

```
~$ cat /proc/cpuinfo
processor       : 0
cpu             : 7455, altivec supported
clock           : 999.999997MHz
revision        : 0.1 (pvr 8001 0201)
bogomips        : 66.30

processor       : 1
cpu             : 7455, altivec supported
clock           : 999.999997MHz
revision        : 0.1 (pvr 8001 0201)
bogomips        : 66.30

total bogomips  : 132.60
timebase        : 33217383
platform        : PowerMac
machine         : PowerMac3,5
motherboard     : PowerMac3,5 MacRISC2 MacRISC Power Macintosh
detected as     : 69 (PowerMac G4 Silver)
pmac flags      : 00000010
L2 cache        : 256K unified
pmac-generation : NewWorld

```

```
~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:15.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Agere Systems FW323
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

```

One of the things that I tried (used to work in Slackware back in the day) was to change the permissions on the audio devices. No luck.

```
~$ ls -l /dev/audio /dev/dsp
crwxrwxrwx 1 root audio 14, 4 2007-01-29 08:34 /dev/audio
crwxrwxrwx 1 root audio 14, 3 2007-01-29 08:34 /dev/dsp

```

```
~$ id
uid=1000(plagued) gid=1000(plagued) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),113(admin),1000(plagued)

```

Anyone have any ideas?

KMix is saying that the sound device is a 'PowerMac Tumbler'



Any thoughts?

---

