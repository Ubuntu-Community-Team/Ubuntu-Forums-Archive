---
title: "New sound card"
date: 2008-12-24
forum: Hardware
---

### Post by shade11 on 2008-12-24
My original setup held an integrated sound card which I generally used to use for everything. I decided to add in a PCI Sound Card (SB Audigy Audio CCE0)which I had laying around, it gives better quality than my integrated card. So I **disabled** the integrated card from my BIOS and put in my PCI card. Ubuntu seems to detect my sound card, though I am not able to hear anything from my speakers.

It works just fine under Windows, though I seem to be having some troubles with Ubuntu. For some reason it gives out no sound whatsoever. 

This card was in my computer before at one point when I had 8.04 installed, it worked just fine (i reinstalled for 8.10). I removed it for other reasons. Reinstalling is **NOT** an option.

---

### Post by gettinoriginal on 2008-12-24
This should solve your problems:  :P

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by shade11 on 2008-12-24
> **gettinoriginal said:**
> This should solve your problems:  :P

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

This did not work, I still have no audio.

---

### Post by kostkon on 2008-12-24
> **shade11 said:**
> This did not work, I still have no audio.
What have you tried exactly from this guide?

Anyway, please give the output of this command
```
aplay -l
```

In Ubuntu 8.10 (and in general, versions >=8.04) audio is controlled by *PulseAudio*. Thus, you need to tell *PulseAudio* which one of card is your default (I am pretty sure *Ubuntu* still sees the on-board one, even if you have disabled it from the BIOS).

So, assuming that you followed the guide, you should have the *PulseAudio Device Chooser* utility installed. Thus, run it (its menu entry is in *Applications &#8594; Sound & Video &#8594; PulseAudio Device Chooser*) and left-click on its icon in the taskbar. Select *Volume Control* and in the *Output Devices* tab you should your PCI card listed (and maybe your on-board one). Right-click on the entry for your PCI card and enable the *Default* option.

If that will not work in all applications and some still produce no sound, then open again the *Volume Control* and in the *Playback* tab you will see the audio stream of the said application. Right-click on it, select *Move Stream...* and then select your PCI sound card to move the audio stream of this application to this card. *PulseAudio* will remember your choice, so you'll not have to do this every time.

Thus, you can use both of your cards, if you like. You can easily move the audio streams of your various applications from the one card to the other with one-click, if it happens that one of your card is connected to different speakers or something like that. Nevertheless, the capability exists, if you want then use it ;)

Hope that helps.

If you have any questions or problems regarding the above, don't hesitate to ask here.

---

### Post by shade11 on 2008-12-25
> **kostkon said:**
> What have you tried exactly from this guide?

Anyway, please give the output of this command
```
aplay -l
```


```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

> **kostkon said:**
> So, assuming that you followed the guide, you should have the *PulseAudio Device Chooser* utility installed. Thus, run it (its menu entry is in *Applications &#8594; Sound & Video &#8594; PulseAudio Device Chooser*) and left-click on its icon in the taskbar. Select *Volume Control* and in the *Output Devices* tab you should your PCI card listed (and maybe your on-board one). Right-click on the entry for your PCI card and enable the *Default* option.

If that will not work in all applications and some still produce no sound, then open again the *Volume Control* and in the *Playback* tab you will see the audio stream of the said application. Right-click on it, select *Move Stream...* and then select your PCI sound card to move the audio stream of this application to this card. *PulseAudio* will remember your choice, so you'll not have to do this every time.

All it says is "ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA"

---

### Post by kostkon on 2008-12-25
> **shade11 said:**
> ```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



All it says is "ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA"

Yes, this is your card. There is a bug whereas emu10k1 based cards (i.e. soundblaster cards) are given a strange name in PulseAudio. Nothing to worry about.

---

### Post by shade11 on 2008-12-25
> **kostkon said:**
> Yes, this is your card. There is a bug whereas emu10k1 based cards (i.e. soundblaster cards) are given a strange name in PulseAudio. Nothing to worry about.

So how do I go about getting audio?

---

### Post by kostkon on 2008-12-25
> **shade11 said:**
> So how do I go about getting audio?
After following the above I said, you didn't get audio?

(Forgot to say, that you need to set your sound playbacks in *System &#8594; Preferences &#8594; Sound* to *Autodetect*.)

If not, then one last thing to check is your hardware volumes. Do you see any icon speaker in your taskbar? If yes, then right-click on it and select *Open Volume Control*. There, your will have to check that your volumes are OK in the *Playback* tab. Also, you can add more available volumes in *Preferences*. Lastly, make sure that the *analog/digital* check-box is not enabled (it should exist in the *Switches* tab).

---

### Post by shade11 on 2008-12-25
> **kostkon said:**
> After following the above I said, you didn't get audio?

(Forgot to say, that you need to set your sound playbacks in *System &#8594; Preferences &#8594; Sound* to *Autodetect*.)

If not, then one last thing to check is your hardware volumes. Do you see any icon speaker in your taskbar? If yes, then right-click on it and select *Open Volume Control*. There, your will have to check that your volumes are OK in the *Playback* tab. Also, you can add more available volumes in *Preferences*. Lastly, make sure that the *analog/digital* check-box is not enabled (it should exist in the *Switches* tab).


I still can't hear anything.

---

### Post by kostkon on 2008-12-25
Try to check again that you have done everything and didn't missed something.


Also, check [this very nice guide]("http://ubuntuforums.org/showthread.php?t=843012"), it has everything in more detail

---

### Post by shade11 on 2008-12-25
> **kostkon said:**
> Try to check again that you have done everything and didn't missed something.


Also, check [this very nice guide]("http://ubuntuforums.org/showthread.php?t=843012"), it has everything in more detail

I'm giving up and reinstalling ubuntu.

---

