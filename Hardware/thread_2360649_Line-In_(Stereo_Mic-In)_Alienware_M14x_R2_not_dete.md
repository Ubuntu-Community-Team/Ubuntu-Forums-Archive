---
title: "Line-In (Stereo Mic-In) Alienware M14x R2 not detected with PulesAudio"
date: 2017-05-06
forum: Hardware
---

### Post by bitfr33z on 2017-05-06
I know there have been a ton of posts about this Laptop and the sound card, but all I can find that has an answer is the headphone jack which I have gotten to work.
I need the Line-In(Stereo Mic-In) Jack to work because I want to be able to pipe my TV sound through my headset. This has been my setup for years when I was using Windows.
A little about the problem:
It is an Alienware M14x R2 with Creative Labs Sound Blaster Recon3Di (CT9570) Sound card.
I have messed with alsamixer until blue in the face.
Audacity does find the jack and is listed as HDA Intel PCH: CA0132 Analog Mic-In2 (hw:0,2); Neutral:0
I've tried all sources from 'pactl list sources' and none of them are what I'm looking for.

So PulseAudio is not loading the device I want to use. I'm imagining Audacity is using alsa to list the devices and interface with them, but how do I get PulseAudio to load that device?

---

### Post by bitfr33z on 2017-05-06
Never mind... I figured this out on my own.
Sorry it was driving me crazy.

For anyone that's having the same problem, easiest solution.

Open a terminal and type:
```
pactl load-module module-alsa-source device=hw:0,2
```

This gives you the Mic input in your sound settings.

If you wish to listen to the input through your speakers or headphones first find the new source number.
```
pactl list sources
```
and the sink number where you want to hear it at.
```
pactl list sinks
```

Then set up a loopback like this.
```
pactl load-module module-loopback source=<Source #> sink=<Sink #>
```

If that doesn't work for others, try getting audacity and finding your device on the input list. All you need to change is the hw:0,2 with the matching one on the audacity list. ( It should be the same though. )
This is a temporary fix, but can be automated through a startup script or setup through PulseAudio's config files. I'm just to tired to figure that out right now.

Just a word of warning: If you use Audacity to record the Line-In, this will interfere with that ability. It's best to set it up as needed, but at least it works for now.

---

### Post by bitfr33z on 2017-05-06
Would still like a better solution to this... The audio quality is bad to say the least. Thinking it's a sample rate problem, but I can't track it down.
If you have a better solution, please let me know.

---

### Post by Bucky Ball on 2017-05-06
Pulseaudio Volume Control is probably going to make your life easier. Forget alsamixer. Install PAVControl from the repositories. Never heard of having to go through all this to get the mic input working. Probably just a tweak in PAVC. The wrong device is possibly set or not enabled in the sound config.

Your devices are clearly visible in PAVC and you might find it easier to configure audio. You may need to experiment a bit to find what works.

---

### Post by bitfr33z on 2017-05-07
Already have PAVControl installed.. It didn't display in there until I linked the alsa-source. That's where the sound distortion is coming from too. It has to do with this laptop's sound card setup... Might be because the jacks are set up to switch functions in the windows drivers. (Stereo Line-In can also be mono Mic-In, Headphone jack can be headset Input and Output.) etc.

---

