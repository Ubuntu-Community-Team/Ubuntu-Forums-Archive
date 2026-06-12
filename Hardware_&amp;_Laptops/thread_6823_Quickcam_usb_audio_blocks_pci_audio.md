---
title: "Quickcam usb audio blocks pci audio"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by swingincelt on 2004-12-01
I have nforce2 audio using alsa and I just bought a Quickcam pro 4000 webcam.

If I boot into Ubuntu with the quickcam plugged in, I don't get any audio.  Actually there appear to be devices missing.

$ aplay
ALSA lib pcm_hw.c:1155:(snd_pcm_hw_open) open /dev/snd/pcmC0D2p failed: No such file or directory
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
aplay: main:507: audio open error: No such file or directory

Here is a list of sound devices when I leave the camera plugged in:
$ ll /dev/snd/
total 0
crw-rw----    1 root     audio    116,   0 2004-12-01 19:07 controlC0
crw-rw----    1 root     audio    116,  32 2004-12-01 19:07 controlC1
crw-rw----    1 root     audio    116,  24 2004-12-01 19:07 pcmC0D0c
crw-rw----    1 root     audio    116,  56 2004-12-01 19:07 pcmC1D0c
crw-rw----    1 root     audio    116,  48 2004-12-01 19:07 pcmC1D0p
crw-rw----    1 root     audio    116,  57 2004-12-01 19:07 pcmC1D1c
crw-rw----    1 root     audio    116,  50 2004-12-01 19:07 pcmC1D2p
crw-rw----    1 root     audio    116,  33 2004-12-01 19:07 timer

If I boot into Ubuntu then plug in the quickcam, my nforce audio works fine.  The quickcam video works either way, and I don't really care about its microphone right now.

Here is a list of devices if I plug in the camera after booting:
$ ll /dev/snd/
total 0
crw-rw----    1 root     audio    116,   0 2004-12-01 19:24 controlC0
crw-rw----    1 root     audio    116,  32 2004-12-01 19:27 controlC1
crw-rw----    1 root     audio    116,  24 2004-12-01 19:24 pcmC0D0c
crw-rw----    1 root     audio    116,  16 2004-12-01 19:24 pcmC0D0p
crw-rw----    1 root     audio    116,  25 2004-12-01 19:24 pcmC0D1c
crw-rw----    1 root     audio    116,  18 2004-12-01 19:24 pcmC0D2p
crw-rw----    1 root     audio    116,  56 2004-12-01 19:27 pcmC1D0c
crw-rw----    1 root     audio    116,  33 2004-12-01 19:24 timer

It seems the devices get initialized in a different order depending on if the camera is plugged in or not.

Can I leave the quickcam plugged in and have everything get initialized properly?

Thanks,
SwinginCelt

---

### Post by gt500 on 2005-01-24
Try looking here ;)

[http://www.ubuntuforums.org/showthread.php?p=55102](http://www.ubuntuforums.org/showthread.php?p=55102)

---

### Post by Buffalo Soldier on 2005-01-24
To swingincelt,

Had the same problem and what I did was add "snd_via82xx" to /etc/modules file.

To gt500,

Sorry I wasn't of much help in solving your problem.

---

