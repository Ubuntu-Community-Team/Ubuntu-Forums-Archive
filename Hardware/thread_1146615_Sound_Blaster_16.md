---
title: "Sound Blaster 16"
date: 2009-05-02
forum: Hardware
---

### Post by MadDawg010 on 2009-05-02
I've installed Xubuntu 9.04 under VirtualBox 2.2.2, and the OS doesn't detect the Sound Blaster 16 card. Sorry, I don't really have any details I can add here.

Any commands/suggestions?

---

### Post by kostkon on 2009-05-02
I assume its an old ISA card, thus you need to see [this how-to here]("https://help.ubuntu.com/community/HowToSetupSoundCards").

---

### Post by MadDawg010 on 2009-05-02
That didn't seem to work at all. When I type this command:

```
sudo modprobe snd-sb16
```

The output was:

> WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa_local, it will be ignored in a future release.

I made another file named alsa_local.conf, but I got the same output, so I deleted it.

I then simply followed the Sound Blaster 16 example:

> EXAMPLE SoundBlaster SB16 non PNP ISA card:

1. Add following line to the /etc/modules file. This will make the driver to load at boot time.
snd-sb16

2. Add following line to the /etc/modprobe.d/alsa_local and /etc/modutils/alsa_local files.
options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5 mpu_port=0x330

Note! Propably alsa_local files does not exist so create them first.
Note! isapnp=0 will turn isapnp off so non pnp card can be found.

Perhaps /etc/modutils/alsa_local is not needed but I did not test.

You can test the driver and the options at alsa_local file without reboot:
sudo modprobe snd-sb16
alsamixer

I made all the files and directories, but I got the same above output.

When I open the mixer (xfce4-mixer, instead of alsamixer) I get this output:

> GStreamer was unable to locate any sound devices. Some sound specific GStreamer packages may be missing. It may also be a permissions problem.

---

