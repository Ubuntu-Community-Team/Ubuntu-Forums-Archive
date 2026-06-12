---
title: "Headset Questions"
date: 2008-08-05
forum: Hardware
---

### Post by Aiello on 2008-08-05
Hello.

I recently purchased a headset with generic microphone and headphone jacks and I have a few questions about getting it fine tuned.

I want to use the headset for talking through Skype, ect. but the sound that comes out of my speakers also comes out through the headset. Also, Skype calls come out through the speakers. Is there anyway to set the headset so that the only sound coming out would be sound from specific applications, such as Skype?

-Thanks!

---

### Post by Moridin333 on 2008-08-05
you would need to set the sound to come out for only the headphone outputs.  This is something that I've found tricky with ubuntu.  The best I can recommend is that you open the volume manager and start playing with the settings.  Also in skype you can select what output and inputs to use.  If ubuntu can identify the different outputs you can select them in skype.

---

### Post by Aiello on 2008-08-05
Well, I have been playing around with different audio settings and nothing seems to fit the bill.
*sigh* The whole reason I bought a headset was to be able to here only Skype through the headset as apposed to it mixing with the others sounds coming from the speakers, which would happen with my old crappy microphone. This is quite annoying.
I will keep trying though.

---

### Post by terry_gardener on 2008-08-06
i have also got an headset tok use with skype in ubuntu hardy the only way that i have found so far to get the sound to come out of the headset while on a call is to open the volume control function by double clicking the speakerr icon at the top right and muting the front speakers and active the headphones in the switch tab, i know this is the best solution but only one that i have found so far.

---

### Post by Aiello on 2008-08-06
This is odd.... it appears that the speakers and the headset are tied together. When I mute "Front" in the ALSA mixer, it mutes both the speakers and the headset.

---

### Post by terry_gardener on 2008-08-06
that's weird when i mute the front option in volume control the speakers mute and when go to the switch tab option and activate and de-activate the headphones they mute or unmute 

sadly i dont a solution if both front and headphone/headset and linked together

---

### Post by Aiello on 2008-08-06
Well, I think I have found what the "name" of the plug-in where the headphone section of the headset is plugged into. Under the Volume Control window, there is device called "Playback: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)".

The only problem is, under the "Sound Diveces, Sound Out" section of Skype, I can only select things that begin with "HDA NVidia).

Now knowing this, do you guys think that it is a Skype problem or an Ubuntu problem?

EDIT: I have just found out that my headset is essentially now useless unless I can get this fixed. Skype will say that there is an error with the audio playback if there is any sound coming through the headset that isn't Skype. 

This is now urgent.

EDIT2: It appears that Skype only has an error with audio playback when certain applications are running. I am going to try to update my sound driver... or something... *sigh*

---

### Post by Aiello on 2008-08-07
Any suggestions?

---

### Post by terry_gardener on 2008-08-07
it seems as so the problem might be with pulseaudio. open the terminal and type "killall pulseaudio" without the quotes and this might solve the issue. 

you can also try open the package manager and install padevchooser and all the requested other things it asks for. 

click applications-sound & video- pulseaudio device chooser and click the jack icon at the top left select the configure local sound server and the tab to the right call simultaneous output and select the option in there to add virtual sound device for simultaneous output. 

hope this works for you

---

### Post by Aiello on 2008-08-07
Thanks! That worked for not hearing Skype! 
I am still stuck with my original problem though.
At least I can USE Skype now! :)

---

