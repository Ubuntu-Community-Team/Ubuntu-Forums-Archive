---
title: "Creative Sound Blaster 5.1 driver Installation help"
date: 2008-11-16
forum: Hardware
---

### Post by varunsuresh on 2008-11-16
Hey

I got the Creative sound blaster 5.1 card (Not the "Live"/Audigy) and have no clue how to get Ubuntu 8.10 to detect the card!
And the system reboots randomly ever since i fixed the card! even if the speakers are switched off for the entire section!
Please help.

---

### Post by kostkon on 2008-11-16
> **varunsuresh said:**
> Hey

I got the Creative sound blaster 5.1 card (Not the "Live"/Audigy) and have no clue how to get Ubuntu 8.10 to detect the card!
And the system reboots randomly ever since i fixed the card! even if the speakers are switched off for the entire section!
Please help.
Live! cards have excellent support (I have the same card BTW) and it should have been recognised right away. Could you be more descriptive, I don't quite understand what problems you have with your sound.

What do you mean by saying that you have fixed the card?

---

### Post by varunsuresh on 2008-11-16
After tryin the aplay -l command it gives me this

varun@varun-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



alsamixer shows this
 Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master  

So i guess the card is getting detected,but there is no output!

---

### Post by kostkon on 2008-11-16
> **varunsuresh said:**
> After tryin the aplay -l command it gives me this

varun@varun-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



alsamixer shows this
 Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master  

So i guess the card is getting detected,but there is no output!
OK, everythings looks fine. I assume then that it is a problem with your volume levels.

First of all, the *alsamixer* utility does not work any more as it's supposed to, since in 8.10 every *ALSA* sound passes through *PulseAudio*. That's why you only get two volumes, the *PulseAudio* playback master and capture master volumes.

The card is recognised fine, so you should have the speaker icon in your taskbar (i.e. the taskbar icon for the *gnome-volume-control* utility).

If so, right-click on it and select *Open Volume Control*. There you will be able to have access to all of the hardware volumes for this card (this card has many. That's a good thing, of course). Try to increase any playback volumes needed, like for example *PCM*, *Master*, etc.

You can enable more available volumes in the *Volume Control* by selecting *Edit -> Preferences* and ticking them.

If you don't have the speaker icon, try to add it by right-clicking on your panel and selecting *Add to Panel*. If you have problem adding it, you can try running *Volume Control* directly by pressing *ALT+F2* and giving
```
gnome-volume-control
```

Also, I recommend you to install the *PulseAudio Device Chooser* (the package is called padevchooser). This will offer you access to all of the features of *PulseAudio*, like individual volumes per application, moving an audio stream from one audio device to another on-the-fly and and some other.

There is also a possibility that is a problem with *PulseAudio*. Maybe your card is not set as the default output device in *PulseAudio*. Thus, run the *PulseAudio Device Chooser* (it will create a menu entry in *Applications -> Sound & Video*) and its icon will appear in your taskbar. Left-click on it and select Volume Control. In the *Output Devices* tab you should see your soundcard. Right-click on it and enable the *Default* option.

Hope that helps.

If you have any question regarding the above, don't hesitate to ask here.

---

### Post by varunsuresh on 2008-11-16
Thanks a lot! it is working! But somehow there is lot of distortion! Do i have to work around some setting?

---

### Post by varunsuresh on 2008-11-16
A loud squeeling noise to be precise! I have to reduce the PCM slider to nearly halfway to get rid of the noise!is there any other way i can get it done?

---

### Post by kostkon on 2008-11-17
> **varunsuresh said:**
> Thanks a lot! it is working! But somehow there is lot of distortion! Do i have to work around some setting?

> **varunsuresh said:**
> A loud squeeling noise to be precise! I have to reduce the PCM slider to nearly halfway to get rid of the noise!is there any other way i can get it done?
That's strange. You should be getting good sound from this card (it of relatively good quality and the drivers are good too). Also, the card and/or its driver is working OK with *PulseAudio*; as least for me.

I have my *PCM* at 100% and my sound is OK. I adjust my sound level using the *Master* volume (I am using my keyboard's volume keys).

Try to mute any inputs, maybe the noise is coming from one of these. Try to add as many inputs you can in the *Volume Control* by selecting *Edit -> Preferences* and then ticking them in order to appear. Some of them will appear in *Playback* tab some in *Capture*.

Mute any input levels in the *Playback* tab, and in *Capture* try to click the speaker icon that every volume has in its base.

Hope that helps.

If your problem is not solved, then it may be *PulseAudio* related. You may need to change the fragments and fragment size in *PulseAudio*.

---

### Post by varunsuresh on 2008-11-22
The noise has disappeared now.The problem is only Front Left and Right speakers work! I tried activating all the switches,only the Master and PCM sliders show response!Changes in any other slider has no effect on the output! :(

---

### Post by kostkon on 2008-11-22
> **varunsuresh said:**
> The noise has disappeared now.The problem is only Front Left and Right speakers work! I tried activating all the switches,only the Master and PCM sliders show response!Changes in any other slider has no effect on the output! :(
Ah, do you mean that you have 5.1 speakers and you want to setup 5.1 sound? If that's the case, you can check this [how-to]("http://ubuntuforums.org/showthread.php?t=795525").

---

### Post by varunsuresh on 2008-11-22
Thanks, all the channels work now,but its all mixed up!
The PCM corresponds to front! The rear satellites work only if the rear jack switch output is set as front,as for the center channel,the lfe and the center both perform the same function!

---

### Post by nivsuj on 2008-11-27
I have a different problem... I have installed ubuntu in windows.I have a Sound blaster 5.1 PCI card.. I don't know why, my ubuntu is not playing audio files.I downloaded all codecs, its playing the file but i cant hear any sound.Am new to linux,so please guide me

---

### Post by kool00702 on 2012-10-27
> **varunsuresh said:**
> Hey

I got the Creative sound blaster 5.1 card (Not the "Live"/Audigy) and have no clue how to get Ubuntu 8.10 to detect the card!
And the system reboots randomly ever since i fixed the card! even if the speakers are switched off for the entire section!
Please help.
       thank you

---

