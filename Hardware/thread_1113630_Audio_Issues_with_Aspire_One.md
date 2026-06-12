---
title: "Audio Issues with Aspire One"
date: 2009-04-01
forum: Hardware
---

### Post by LzBy1 on 2009-04-01
Hi, I'm fairly new to linux. I just bought an Acer Aspire One 150 and installed Intrepid Ubuntu 8.10 on it via Wubi installer (works great) then installed Netbook Remix (also great).

I'm currently running Ubuntu on the -7 Kernal, to fix the ethernet (Kernal -11 causes issues, waiting on the next kernal upgrade, maybe it will resolve this), I also fixed the wireless issue (another known bug).

The last thing on my list is fixing the audio, I don't have any audio at all, ether through headphones or the speakers. When audio is supposed to be playing all I hear is a slight crackling.

Summery:
*Acer Aspire One AOA 150-1504
*no audio at all
*crackling sound through speakers
*drivers seem to be installed
*PC beep works (don't know if that's related)
*Ubuntu 8.10 -7 Kernal

I followed the steps here [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) - didn't help.

I included a screen shot of the audio mixer and the different choices it gives me. 

Please help, I have come across several other forums on the web with people with similar issues, however, most with different model computers. According to most of the topics i have read, I shouldn't be having problems, with 8.10 the audio SHOULD work out of the box, however, that is obviously not the case and also not very helpful.


[IMG]http://www.mediafire.com/imgbnc.php/7588787d1c330acbcbdba41493be23032g.jpg[/IMG]

Also:
From
```
aplay -l
```
I get
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
and from
```
lspci -v | less
```
I get
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Device 015b
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 58540000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

Thanks.

---

### Post by LzBy1 on 2009-04-04
```
chris@ubuntu:~$ tail /var/log/messages
Apr  4 13:47:59 ubuntu kernel: [   77.608885] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr  4 13:47:59 ubuntu kernel: [   77.695556] NET: Registered protocol family 17
Apr  4 13:47:59 ubuntu kernel: [   77.790429] mtrr: no more MTRRs available
Apr  4 13:48:18 ubuntu pulseaudio[5398]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr  4 13:48:18 ubuntu pulseaudio[5400]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr  4 13:48:18 ubuntu pulseaudio[5400]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr  4 13:49:31 ubuntu kernel: [  170.194154] NET: Registered protocol family 10
Apr  4 13:49:31 ubuntu kernel: [  170.200778] lo: Disabled Privacy Extensions
Apr  4 13:49:31 ubuntu kernel: [  170.202915] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  4 14:07:49 ubuntu -- MARK --

```

---

### Post by miguelquiros on 2009-04-10
Hello. In my case (I do not know if it is your problem also), two different drivers are loaded for the same card: snd_pcsp and snd_hda_intel. I managed to solve the problem avoiding the first one to load, this is done by adding the following line to the file /etc/modprobe.d/blacklist:
      blacklist snd_pcsp
After this, sound comes out of the computer, nevertheless recording still does not work.

Good luck!

---

### Post by teaker1s on 2009-04-10
you can specify model for hda intel, this is done by
```
sudo gedit /etc/modprobe.d/options
```

We then want to add this line to the bottom of the file
```
options snd-hda-intel model=acer-aspire
```

Save...

---

### Post by LzBy1 on 2009-04-12
Hey, guys I wanted to thank you for all your help and input.

Problem Resolved!!!

I tried both of your advice, nothing seemed to work and finally I got frustrated and did a completely fresh install, once again using Wubi from Windows XP (I know NTFS sucks right, well... i'm lazy, didn't want to reformat) anyway, for whatever reason the audio worked out of the box (8.10 w/-7 kernal). Updated, and to my surprise the audio AND THE LAN both worked with the -11 kernal. I wasn't aware they fixed the bug in an update, since it was the update that caused the problem in the first place. I fixed the audio and usual (madwifi) and the wireless LEDS the installed netbook remix... everything is running great, perfect audio, although it still probably can't record (I haven't tested it) but that's a known bug I can live with.

So my advice would be (if you are experiencing the same audio problems on the acer aspire one) to try a fresh install.

Thanks.

---

