---
title: "Asus VivoBook Max x541u"
date: 2016-12-21
forum: Hardware
---

### Post by danieldsj on 2016-12-21
I just recently got a really good deal on a Asus VivoBook Max x541u and I had to implement several workarounds to get it to work with Ubuntu.  I thought I would share it in the forums for future self if I ever find myself re-installing Ubuntu (for whatever reason), or anyone else that purchased this model of laptop.

**RE: Cannot install or boot due to out of space errors**
The default kernel logging for some pcie devices generates a lot of events which I believe caused the root partitions to fill up when performing an install or a live boot. Before you can install Ubuntu onto this system you need to use the *pcie_aspm=off* kernel option to suppress the events.

**RE: Microphone not picking up sound**
Edit the */etc/pulse/default.pa* to include *load-module module-alsa-source device=hw:0,0* before the *.ifexists module-udev-detect.so* line.
Also, I had to write a small script in */usr/local/bin* that is invoked by a systemd module at boot time to ensure that the audio levels were correct, the script contained the following commands:

```

hda-verb /dev/snd/hwC0D0 0x1a SET_AMP_GAIN_MUTE 0x5003
hda-verb /dev/snd/hwC0D0 0x1a SET_AMP_GAIN_MUTE 0x6003
hda-verb /dev/snd/hwC0D0 0x23 SET_AMP_GAIN_MUTE 0x5200
hda-verb /dev/snd/hwC0D0 0x23 SET_AMP_GAIN_MUTE 0x6200
hda-verb /dev/snd/hwC0D0 0x08 SET_AMP_GAIN_MUTE 0x503f
hda-verb /dev/snd/hwC0D0 0x08 SET_AMP_GAIN_MUTE 0x603f
hda-verb /dev/snd/hwC0D0 0x08 SET_POWER_STATE 0
hda-verb /dev/snd/hwC0D0 0x1a SET_POWER_STATE 0

```

Reference: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1596381](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1596381)

I may find some other quirks and will try to add it to this forum.

---

### Post by mörgæs on 2016-12-22
Thanks for posting. If you add a note to the [compatibility list]("https://ubuntuforums.org/showthread.php?t=1543006") there is a bigger chance that people will find your advice.

---

### Post by gwambai on 2017-05-07
Thanks for the advice! I had the same problems booting on my vivobook u541 and setting pcie_aspm=off did the trick.  For anyone else out there who doesn't know exactly how to do that I found this guide very helpful:  [https://ubuntuforums.org/showthread.php?t=2303880](https://ubuntuforums.org/showthread.php?t=2303880)

---

