---
title: "Sound Card Problems -- Please Help!"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by sarsippius on 2007-05-29
Hey all,

I have an Audigy 2 ZS card in my computer.  I am not getting any sound from it.  I followed this guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) as best as I could.

By the time I got to the bottom I still don't have any sound.  This is really frustrating me!

If anyone can please help me out, I would really appreciate it.

Here is what I get with the aplay -l command

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


My Sound card shows up here, and under System, Prefs, Sound.  But when I try to play any system sounds or Amarok I get nothing!

---

### Post by Boris-- on 2007-05-29
I've had a simmilar problem with my Sound blaster. What I did was mess with the priorities of the soundcards (you should put the Audigy on 0). How to do this? 
[B]
Note: This section assumes that you have installed each soundcard properly.

    *
      In a shell, type
      Code:

      cat /proc/asound/modules

    *
      This will give the the name and index of each soundcard you have currently. Make a note of the names, and decide which one you want to be the default card.

    *
      Now type
      Code:

      sudo nano /etc/modprobe.d/alsa-base

    *
      At the very end of the file, add the following (assuming you have 3 cards with module names A, B and C and you want to have them in the order CAB)

Code:

options snd-C index=0
options snd-A index=1 
options snd-B index=2
[/B]

find out more @ [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+audio+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+audio+guide)

hope this helps!

oh, and when you change the priorities, the sound will start working after the restart. If it still doesn't work, check alsamixer and audio permissions or Gnome audio section (the obvious stuff).

---

### Post by B-Con on 2007-06-09
Sweet, that worked for me too. Cheers.

---

