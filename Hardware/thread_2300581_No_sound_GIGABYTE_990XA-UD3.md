---
title: "No sound GIGABYTE 990XA-UD3"
date: 2015-10-26
forum: Hardware
---

### Post by Matti_Ranta on 2015-10-26
Everything works fine with my machine but I have never managed to get sound out of that motherboard. I have tried Lubuntu, Mint, Xubuntu and some other Ubuntu distros. Those have had weird problems. Like freezing all of the sudden etc. Only Ubuntu 14.04 LTS has worked well. Except no sound coming out no matter what. I think the problem is the motherboard. It was propably rushed out with suboptimal bios etc. I have tried to fix it before uninstalling and installing stuff only to break everything and reinstall Ubuntu. The easiest way would be to get rid of the motherboard and buy Asrock like I intended but they were out of stock. I have the latest BIOS. No newer anyway. The music chip in REALTEK ALC889. Any tricks I can try without having to reinstall OS and download these big updates n+1 times?

---

### Post by Matti_Ranta on 2015-10-27
Hello
Is anyone using or has used GIGABYTE 990XA-UD3 motherboard succesfully with any Linux flavour? Has gotten sound out and other things has worked well too? Or gotten sound out of Codec: Realtek ALC889 on any motherboard?

I have researched the issue and the sound chip isn't supported I guess.

---

### Post by QIII on 2015-10-27
I have a 990FXA-UD3 with the same audio hardware.  It works fine.

Are you using ALSA or PulseAudio?

---

### Post by Matti_Ranta on 2015-10-27
> **QIII said:**
> I have a 990FXA-UD3 with the same audio hardware.  It works fine.

Are you using ALSA or PulseAudio?

Hello
Which OS are you using? I could try it too. Yes ALSA and Pulseaudio are all installed, activated and work with a soundcard. Softwarewise everything seems to work but I don't get sound out of the motherboard's audio no matter what. I have to check the chip physically whether it is totally dead. I get sound out from a soundcard but I would prefer that the motherboard's audio would work too

---

### Post by QIII on 2015-10-30
This is on Wily.  I checked it again just now while I was testing the AMD driver bug on that machine.

Which of the two are you using:  ALSA or PulseAudio?

---

### Post by teodoro-piccinni on 2016-02-06
I have the Gigabyte 990FXA-UD3 rev.1.0, it worked with any previous version of Ubuntu, but with 15.10 I found the same issue. Once installed it worked well with 2.0 channel, then I tried to configure the 5.1 speaker but it didn't worked and I lost the default configuration.
Now I can hear no sound if I use Rhythmbox, Totem, Firefox, etc...

I tried the following command and everything works as expected, but media reproduction is still mute:
speaker-test -Dplug:surround51 -c6 -l1 -twav

Someone know how to find the right source of sound and set it as default for the system?

Thanks in advance

---

### Post by teodoro-piccinni on 2016-02-06
Ok, the problem is that the system detect the analog output as unplugged. I installed PulseAudio Volume Control (apt://pavucontrol) and I forced my desired output even if it is labeled as unplugged. Now everything works.

---

