---
title: "Audio stop working after new install"
date: 2010-12-15
forum: Hardware
---

### Post by Brausen on 2010-12-15
I have installed Ubuntu 10.10 in my Acer 7736-6948 and the audio stop working.
That's my configurations:

```
$ lshw -c sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: **82801I (ICH9 Family)** HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:f4700000-f4703fff

```

```
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: **Realtek ALC888**

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#3 <==
Codec: Intel Cantiga HDMI

```

```
$ lspci -k
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0296
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I have tried all possible combinations in alsa-base.conf but it doesn't work.

In syslog I got this message:
```
pulseaudio[1644]: alsa-util.c: 
snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 80.

pulseaudio[1644]: alsa-util.c: 
Most likely this is a bug in the ALSA driver 'snd_hda_intel'. 
Please report this issue to the ALSA developers.

```

Someone can help me?

---

### Post by dabl on 2010-12-15
Verify that the main (PCM) channel is not muted.

Then you probably need to review this:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and look for your model of Acer here:

[http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database](http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database)

---

### Post by Brausen on 2010-12-16
dabl, the main channel is not muted.. and I have tried all acer models. No success!

I don't know what to do.. maybe I should try reinstall 10.04

---

### Post by Brausen on 2010-12-16
My audio card is working again.

I followed this instructions:
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

And I added the two lines below at the end of alsa-base.conf:
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

---

