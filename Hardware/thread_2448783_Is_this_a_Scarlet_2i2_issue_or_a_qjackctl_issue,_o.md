---
title: "Is this a Scarlet 2i2 issue or a qjackctl issue, or???"
date: 2020-08-13
forum: Hardware
---

### Post by Dirk_Ouellette on 2020-08-13
Mic and two keyboards through Scarlet 2i2 interface, shows up fine in Reaper 6.113, but when recording, very tiny signal with minimal to no output in the recording once supposedly recorded.
What messages should I post to help solve this? I am running UbuntuStudio through qjackctl from the Scarlet and from the Scarlet to my powered speaker.
The signal from the two keyboards plays great through the speaker, but even as the signal shows up on both tracks in Reaper, one track for the mic, and one for the two keyboards, there is no output to the speaker from the mic???
Is this a Scarlet issue or a qjackctl issue, or???

---

### Post by slickymaster on 2020-08-13
*Thread moved to **Hardware**.*

---

### Post by Bucky Ball on 2020-08-14
When you play one of the keyboards, the volume meter is moving on the correct Reaper input track? You have the input on the Reaper track set to the correct input device? If you are playing the keyboard through the speakers when you are recording and the mic is live/recording too, is the keyboard being recorded on the MIC track, not the keyboard track and that's what you're faintly hearing? Maybe sound like silly questions, but best to ask.

It is hard to figure out the issue without knowing all of the settings you have set up in Reaper. If audio is getting through at all to Reaper, then JACK is working its magic. (PS: Launch JACK first, then Reaper, but you probably know this. :)) Also, check you have the Scarlett selected as your input/output source in JACK, presuming you are outputting from the computer to the Scarlett and then to the speakers. That's in 'Setup'.

When you're playing back the recorded tracks, what volume do you have the track volume slider in Reaper set at? At full volume is it still too quiet? That might indicate that the volume of the input device is too quiet during record or that it is being recorded through a live mic. You see action on the meter of the correct track? 

Ideally, you want to set your recording levels and get them right prior to doing any recording. Suggest you unplug everything from the speakers. That will confuse the issue. Plug one keyboard into the Scarlett, assign that to a track in Reaper, set the volume fader on the Reaper keyboard track and the master volume fader on Reaper to 0dB, then turn the volume of the KEYBOARD up ON THE KEYBOARD until you get to orange on the meter (not red) on the track meter in Reaper. Once you're there, that keyboard is good to go recording. Set the volume slider in Reaper to where you want it and start on the next keyboard. Then the mic.

Once you've done this pre-record setup, you can use it as a template for future sessions. You know your keyboards, at least with the original sounds you used to set up, are at the perfect volume for recording.

Finally, get the input volume from the external device right before tweaking the volume slider in Reaper. Just set that to 0dB for now and forget about it. You will find that tweaking volumes in Reaper live will bring the volume to your ears up and down, but the level meter will remain the same because that is being driven by the input device (your keyboard or mic). Sorry if I've repeated myself on that, but it's an important point that can cause confusion.

Don't know if that will get you any further, but here's hoping. Good luck.

---

### Post by Bucky Ball on 2020-08-14
Okay, having previously tried it in Windows, I just launched Reaper for the first time in Xubuntu and it may be your JACK settings after all. Try this.

Launch then start JACK. Launch Reaper. In Jack, go to Setup> Settings tab. Driver: alsa. MIDI driver 'none'. I have Realtime ticked. The samplerate and buffer will depend on what suits your setup.

Go to Advanced tab. Output Device on the right should be set to the Scarlett. So should Input Device. Leave Channels and Latency I/Os as default. Close that window.

Now click 'Connect' button on the JACK GUI. Is your interface in Audio tab as 'System'? It should be. Click the arrow next to System. Does it have the same number of inputs and outputs as your device? You should also see Reaper in the I/O columns. 

Here's the important bit. Under System in the Output Ports column on the left, click the capture channel on the Scarlett that you have your keyboard plugged into. With it highlighted, go to the Input Ports column, click Reaper and highlight the playback channel of your choice, then click 'Connect' in the bottom right corner. 

If you have the keyboard stereo in 1/2, say, you would need to connect capture 1 from System to playback 1 on Reaper, then 2 to 2. Unfortunately, I haven't found a way to connect more than one at a time. 

Now see what you get in Reaper. Hope that helps.

---

