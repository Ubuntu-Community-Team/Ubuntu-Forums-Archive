---
title: "Sound/No Sound issues"
date: 2008-12-23
forum: Hardware
---

### Post by MR2Quick on 2008-12-23
When i turn on the laptop, i get the quick bongo sound (or whatever instrument that is) like i always have.  

When i enter in my login information, instead of playing the happy clickity-clack drums sound it used to, it now sounds like someone is ripping a piece of paper.  (Riiip.....rip.....RIIIIP)

If i load up the Sound Preferences, i changed ALSA to HDA Intel ALC660-VD Analog (OSS) and I get the tone without the preferences crashing.  But there is no sound in anything in the browser (pandora or youtube tested)  

Volume is turned up on everything i can find.  I don't know exactly why my sound disappeared, i haven't had this issue in the past.

Any suggestions?  Asus F8Sn-C1 running Latest version of Ubuntu (and just did an update today to double check)

---

### Post by jfmxl on 2008-12-24
The computer I used daily running 7.10 crashed and I set up anther. I could never record sound on that one under ubuntu, but I could play it. I decided to install 8.10 on the machine I brought up to replace the other. Thanks to the NEW! IMPROVED! Ubuntu 8.10 OS I can no longer hear sound at all. Can't record it either.

I keep a ten year old laptop running windows 2000 next to my ubuntu hardware. When I have to record sound, or now, listen to it... I use that.

Someday linux will get it together. Just not today.

Don't ask me why I keep using it. I can't give you a rational answer.

---

### Post by joe74 on 2008-12-24
It's just similar to the issues I have with alsa sound system.

Try cheching System>> Administration >> Services then look for sound services, it should be with a check on it.

You can also try on logging in the session as "Failsafe GNOME". This is the only way I have sound in my laptop. It's the only way, so far.

---

### Post by joe74 on 2008-12-24
Must I say that I have recorded both audio an video with linux. There's nothing linux can envy M$ software... Must I say it's all the opposite. Regards.

---

### Post by jfmxl on 2008-12-26
Here's what I have after clicking System/Sounds
 Sound Events 
  sound playback	autodetect *
  			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (ALSA)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			ALSA Advanced Linux Sound Architecture
			OSS Open Sound System
			PulseAudio Sound Server
			
 Music and Movies 
  sound playback	autodetect *
  			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (ALSA)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			ALSA Advanced Linux Sound Architecture
			OSS Open Sound System
			PulseAudio Sound Server
			
 Audio Conferencing
  Sound playback	autodetect *
  			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (ALSA)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			ALSA Advanced Linux Sound Architecture
			OSS Open Sound System
			PulseAudio Sound Server
  
  Sound capture	VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (ALSA)
			VIA 82C686A/B rev50 with VIA612A VIA 82C686A/B rev50 (OSS)
			ALSA Advanced Linux Sound Architecture
			OSS Open Sound System
			PulseAudio Sound Server
			Test Sound
			Silence
			
 Default Mixer Tracks
  Device		Capture: ALSA PCM on front:0 (VIA 82C686A/B rev50) via DMA (Pulse Audio ...
			Capture: Monitor Source of ALSA PCM on front:0 (VIA 82C686A/B rev50) vi ...
			Playback: ALSA PCM on front:0 (VIA 82C686A/B rev50) via DMA (Pulse Audio ...
			VIA 82C686A/B rev50 (ALSA mixer)
			VIA Technologies VIA612A (OSS Mixer)

Trying all combinations in turn and clicking test yields silence in every case. I wonder if anyone can suggest a next step in my attempt to have Ubuntu 8.10 first produce sound and second record sound? Thanks for any help that may be given.

---

### Post by jfmxl on 2008-12-26
All else failing... I checked the plugs on the back of the box and discovered my headphones were plugged in incorrectly. 

I have sound. Hurray! 

Still cannot record. If I am able to fix that, I will report back. But I was unable to fix that after many attempts with 7.04 and 7.10 so I am not optimistic. 

But I can listen to Mozart while I try... and leave my venerable old laptop turned off 'til I have to record something for my students,

Thanks for your help.

---

### Post by jfmxl on 2008-12-27
I have made progress. I was able to record sound in audacity. But the only way I could tell that was the case was to watch the VU meter. The recording level was so low that I would have to amplify the signal to hear it... +30db or more.

I found no way to adjust the volume from sudacity, or from alsamixer, or alsamixergui. But using an application called soundrecorder under Applications -> Sound and Video, and selecting File -> Open Volume Control -> Preferences allowed me to check '+ Mic Boost' which opened a tab called Switches Volume Control -> Preferences window wherein I again checked 'Mic Boost (+20db)'.

Now at least the recording is audible. I can use audacity to amplify it further as required.

This machine uses a VIA chipset, which does seem to be supported by Ubuntu. But my "real machine" will someday be back in service and I fear that its Nvidia chipset will still not support recording.

But at least I will be able to keep this linux to record on, dropping the W2k laptop from the equation. Progress, of a sort.

Thanks again for your help.

---

