---
title: "The microphone doesn't work with Creative Sound Blaster Live! Platinum! 5.1"
date: 2010-06-09
forum: Hardware
---

### Post by matrobriva on 2010-06-09
Hello everyone! I'm new here!
I have a serious problem with my sound card and Ubuntu 10.04. In the  others distros (Gentoo, Sabayon, Fedora, Puppy...) the mic run very  good, but in Ubuntu i can't record any sound. I can ear the sound exit  from the speaker, but with sw like Sound Recorder, Audacity and Skype i  can't record the sound. I tried EVERY setting in alsa mixer/Gnome alsa  mixer but I can't resolve the problem. I attach the outpout of some  commands:

    Lspci:

    04:03.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1  (rev 07)
    04:03.1 Input device controller: Creative Labs SB Live! Game Port  (rev 07)



    Aplay -l:



    **** Lista di PLAYBACK dispositivi hardware ****
    scheda 0: Live [SB Live! 5.1 [SB0060]], dispositivo 0: emu10k1 [ADC  Capture/Standard PCM Playback]
      Sottoperiferiche: 32/32
      Sottoperiferica #0: subdevice #0
      Sottoperiferica #1: subdevice #1
      Sottoperiferica #2: subdevice #2
      Sottoperiferica #3: subdevice #3
      Sottoperiferica #4: subdevice #4
      Sottoperiferica #5: subdevice #5
      Sottoperiferica #6: subdevice #6
      Sottoperiferica #7: subdevice #7
      Sottoperiferica #8: subdevice #8
      Sottoperiferica #9: subdevice #9
      Sottoperiferica #10: subdevice #10
      Sottoperiferica #11: subdevice #11
      Sottoperiferica #12: subdevice #12
      Sottoperiferica #13: subdevice #13
      Sottoperiferica #14: subdevice #14
      Sottoperiferica #15: subdevice #15
      Sottoperiferica #16: subdevice #16
      Sottoperiferica #17: subdevice #17
      Sottoperiferica #18: subdevice #18
      Sottoperiferica #19: subdevice #19
      Sottoperiferica #20: subdevice #20
      Sottoperiferica #21: subdevice #21
      Sottoperiferica #22: subdevice #22
      Sottoperiferica #23: subdevice #23
      Sottoperiferica #24: subdevice #24
      Sottoperiferica #25: subdevice #25
      Sottoperiferica #26: subdevice #26
      Sottoperiferica #27: subdevice #27
      Sottoperiferica #28: subdevice #28
      Sottoperiferica #29: subdevice #29
      Sottoperiferica #30: subdevice #30
      Sottoperiferica #31: subdevice #31
    scheda 0: Live [SB Live! 5.1 [SB0060]], dispositivo 2: emu10k1 efx  [Multichannel Capture/PT Playback]
      Sottoperiferiche: 8/8
      Sottoperiferica #0: subdevice #0
      Sottoperiferica #1: subdevice #1
      Sottoperiferica #2: subdevice #2
      Sottoperiferica #3: subdevice #3
      Sottoperiferica #4: subdevice #4
      Sottoperiferica #5: subdevice #5
      Sottoperiferica #6: subdevice #6
      Sottoperiferica #7: subdevice #7
    scheda 0: Live [SB Live! 5.1 [SB0060]], dispositivo 3: emu10k1  [Multichannel Playback]
      Sottoperiferiche: 1/1
      Sottoperiferica #0: subdevice #0



    cat /proc/asound/card0/codec97#0/* | grep -i codec

    Extended ID      : codec=0 rev=0 SDAC DSA=0



    dmesg | grep -i hda


no results


    ps aux | grep pulse


    1000      1380  0.0  0.2  94596  4960 ?        S<sl 18:47   0:00  /usr/bin/pulseaudio --start --log-target=syslog
    1000      1407  0.0  0.1  10748  2992 ?        S    18:47   0:00  /usr/lib/pulseaudio/pulse/gconf-helper
    1000      2730  0.0  0.0   3340   896 pts/0    S+   19:18   0:00  grep --color=auto pulse

Any idea? 

PS: The chipset of the sound card is Emu10k1
PS2: Sorry for my bad english!

---

### Post by endo on 2010-06-09
I can confirm this. I have exactly the same problem with exactly the same soundcard!
Ubuntu 10.04 Lucid 64 bit
Input doesn't work at all, not even one of the channels. That's pretty annoying :(

As far as I know, the kernel driver for this sound chip emu10k1 has been pretty stable for a very long time, the same soundcard with the same kernel module worked like a charm on Hardy Heron, all inputs worked fine.

I think it's not a pulseaudio problem, because suspending (pasuspender) pulseaudio doesn't change anything. I even tried uninstalling the whole pulseaudio system, but that didn't fix the problem either. Sound played good (bare ALSA), but input still didn't work.

I'd be very happy if someone could give me a clue on solving that problem...

---

### Post by lidex on 2010-06-09
For Audacity, and perhaps a clue to other programs:
[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044]("http://forum.audacityteam.org/viewtopic.php?p=75044#p75044")

---

### Post by matrobriva on 2010-06-11
No, your solution doesn't work.

If I amplify the sound recorded by audacity i listen my voice very low, with horrible rumors ](*,)

---

### Post by endo on 2010-06-12
I think we all agree that sound input is totally broken in Ubuntu 10.04 with Creative SB Live! and I rather think it's an ALSA problem.
I just don't understand why the ALSA guys had to break something that worked perfectly well on older versions for a very long time?
I just don't feel like spending $300+ for a new ASUS Xonar card just to have input working :/ And Creative X-Fi sucks. Really.

---

### Post by matrobriva on 2010-06-12
Yes, it's true... Now I use for recording an old sound card ISA, but the quality is very low :mad:

---

### Post by TiGR on 2010-11-04
This has worked for me: [http://ubuntuforums.org/showthread.php?t=1477261](http://ubuntuforums.org/showthread.php?t=1477261)

After I've install that, I had to reboot, select hdmi in skype settings for mic, and disable mic boost from mixer settings.

---

