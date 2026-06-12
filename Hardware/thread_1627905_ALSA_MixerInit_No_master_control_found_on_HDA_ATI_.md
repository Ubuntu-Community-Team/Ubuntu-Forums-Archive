---
title: "ALSA_MixerInit No master control found on HDA ATI HDMI"
date: 2010-11-22
forum: Hardware
---

### Post by bstacker on 2010-11-22
Hello everyone,

I know when people read my post title I'll probably get told to go search the forums, as this seems to be a fairly common issue, but I have searched and found no working solutions.

As listed in the post title, when running winecfg from the terminal the output I receive is:

```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer

```
I noticed that when I attempt to run Diablo 2 through Wine, I have sound through the first two loading screens, but as soon as I enter the actual gameplay, the sound is gone.  I checked all the settings in-game to make sure they were appropriately set, and they were.

In the winecfg window, under the audio tab, I have the following available under ALSA.

Wave Out Devices: default
Wave In Devices: default
MIDI Out Devices: MIDI through Port-0
MIDI In Devices: MIDI through Port-0
Mixer Devices: HDA ATI SB

I've also run this:
```

cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf8600000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf8010000 irq 45

```

It seems to me the easiest solution would be to disable the HDMI device completely as I never use it, but I'm not sure how I would go about doing that.  Otherwise, if I could just force Wine to always and only use the SB device, that might work as well.

I'd definitely appreciate any advice anyone has to offer.

Thanks!

---

### Post by bstacker on 2010-11-22
Interesting update.

After following the guide on OpenSound to switch from ALSA to OSS, the problems seems to be resolved.  HOWEVER, at the cost of my volume control.

Still looking for a solution to have ALSA working, but I'm also working on trying to get my volume controls back in OSS if that will work as a permanent remedy.

---

### Post by bstacker on 2010-11-23
Switched audio acceleration to Emulated from Full and resolved the issue.
Marking as solved.

---

### Post by neselain on 2010-11-25
Thanks a lot for your help and sharing.  I too am having this problem, only installing TextAloud in wine.  Welllll, looks this isn't working for me.  Still looking.

---

