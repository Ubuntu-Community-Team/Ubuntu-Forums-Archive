---
title: "Audio Feedback - Make it stop!"
date: 2008-11-06
forum: General Help
---

### Post by phorgan1 on 2008-11-06
On a lenovo T60p using Ibex, when listening through the built-in speaker and turning the volume up, I get LOUD and unpleasant audio feedback.  Great, I thought, good to know that my microphone is turned on, so I brought up a handy mixer control and turned down and muted all the recording inputs.  BUT!!!  You guessed it, I still get the pernicious feedback, (and I don't mean that the computer critiques my clothing choice of the day) !   Whether they call it input or capture, every volume or mixer application shows that the microphone is turned down and muted, to no avail.  I thought it might be some sort of software loop, but using the headphone with the volume turned up more than sane yields no feedback.  I tried covering the hole in the  case that goes to the mike, to no effect, but since the mike's in there with the speaker I didn't have much hope of that.  I wish there was a physical switch to turn off the mike so that I could verify that it's the source of the feedback, but there's not.  Does anyone have a guess/path/suggestion/clue/plan to take over the world?

patrick

---

### Post by mindgrind on 2008-12-28
yeah. on hardy i get very low speaker volume and when i turn up the volume i get horrible feedback squeal.  i've tried to change settings to pulseaudio, alsa, and autodetect, but no joy.  any thoughts?  lenovo thinkpad x60s

---

### Post by randallecook on 2008-12-28
It could be that the audio output is being routed to the input internally, bypassing the microphone and going straight to the A/D converter. This is a typical configuration when you want to rip DRM'd content--you effectively just re-encode what is going out to the speaker. I am not sure this is what is going on with your system, but it could explain the feedback. I am not familiar with your hardware but hopefully this will lead to another avenue to explore.

I have found with my system that I had to turn the wave output level down quite a bit to get audio playback without distortion--even when the master volume was low. I think some software in there was not mixing the signals well. Perhaps there is a flaw in the handling of the audio input, too.

Randall

---

### Post by Peter09 on 2008-12-28
Try muting the mike rather than turning the volume down - worth a try

---

### Post by platinumlolita on 2009-08-11
I'm sad there's no decent answer on here. I'm in Xubuntu on a Dell Mini 9 (Vostro A90) and I get this type of thing on low levels of audio, even when there is absolutely no media program running (ie Songbird, Amarok). It really bothers me, especially when I'd like to listen to music during work. Somebody do follow up!

Muting works, but I can't listen to music. :confused:

---

### Post by mubes on 2009-09-11
In the Volume Control applet, on the 'Playback' side, Mute your microphone - you don't want your microphone playing back immediately, that causes feedback (as you've found).

DAVE

---

### Post by platinumlolita on 2009-09-11
I tried everything! Everything that doesn't have to do with playback of audio is completely muted. But oh well. I guess I'll use my iPod instead... ](*,)

---

### Post by analkant on 2009-09-16
I have the same error, and, based on the idea that it's a loop from poorly routed source audio, have turned down the capture audio, which does stop the feedback just as muting PCM or AC97 does. of course, i can't hear anything this way. Anyone who knows more about the way that driver routes audio have an idea?

---

### Post by analkant on 2009-09-16
I'm running Xubuntu Jaunty and, after reading several descriptions of this problem and similar ones, on here [http://ubuntuforums.org/showthread.php?t=333478](http://ubuntuforums.org/showthread.php?t=333478), have noticed that this problem seems to be an incompatibility with SoundBlaster's card, which is also what I have. I just installed banshee on here before this happened, but removing it via terminal has not helped. 
I've played around with the capture and switches options, and have noticed it only happens when Capture isn't muted (the other captures can be muted or at full, it makes no difference), and when AC97 and PCM are both at reasonable volume. Also, soundblaster has to be on Mix, rather than video capture or something else.
When I turn on Mix and check the Tone box, the pitch of the feedback changes drastically, but it's still there and I still can't hear any actual audio. 
I've tried basically every combination of on/off for everything. Changing settings on the other sound cards offered (Intel and analog devices) don't affect the feedback at all, but I also can't seem to switch to use them instead of Soundblaster. Anyone know how to do this?

---

### Post by analkant on 2009-09-17
So, as with many people, I discovered some better solutions to this issue by searching the multimedia forum. The one that worked for me was installing pulseaudio volume control (and device chooser), then going to devices and setting one sound card to default and the other one to mute. I then set the AC97 level on the default sound card to mute, and the rest of the controls to regular, sensible levels. The one problem I have now is that the default sound card is muted every time I boot the computer. I unmute it and it works fine. Someone suggested changing my sound cards in my BIOS, but all I can see related to my sound cards is IRS numbers, and I'm afraid to change those, and there's definitely no default or delete setting in there. Anyway, thought I'd share for anyone else coming here from Google.

---

### Post by theozzlives on 2009-09-17
> **analkant said:**
> I have the same error, and, based on the idea that it's a loop from poorly routed source audio, have turned down the capture audio, which does stop the feedback just as muting PCM or AC97 does. of course, i can't hear anything this way. Anyone who knows more about the way that driver routes audio have an idea?

Try muting your inputs and microphone some input source is probably to close to your speakers (like the feedback of a screeching guitar during a concert).

---

### Post by analkant on 2009-09-25
Obviously, the first thing I (and many people on here, I'm sure) did was make sure my microphone was neither on nor plugged in (and I have no other external input sources, but I muted everything else). Still not sure why my sound is always muted when I turn the machine on (and why Rhythmbox only recognizes CDs after I click it in the "removable drives and media" section).

---

### Post by rreese6 on 2009-09-25
Not sure if this will be useful since I run Xubuntu 8.04, however I have found before that the mixers just don't seem to be in total control of the sound cards.
What I do to make "real" settings is run alsamixer in a terminal
the "h" key will bring up help, tab will show you different function screens, arrow move you to columns and the < and > key make slections.

See if that helps.

From the terminal (console, shell, etc) type.

```
alsamixer
```

---

### Post by analkant on 2009-12-07
To clarify my earlier post,
here is what you do if you either
1. have no sound or
2. get loud feedback
when running jaunty 

check if you have a soundblaster soundcard AND another soundcard installed (mine is an Intel card)

If so, the problem is that your machine is confused as to which soundcard to use. 
One solution would probably be to physically remove the other soundcard (the Intel one, in my case)
but that sounds like a pain and I haven't tried it so can't recommend it.
What I did was install Pulseaudio device chooser and pulseaudio volume control
Then I changed the default soundcard to Soundblaster using the device chooser I think
Then I opened the mixer and set the Soundcard at the top to Soundblaster
then changed AC97's volume level to 0 (or mute it)
I turned on Capture and put its volume all the way up
then I went to the Switches tab and set it to Mix
Obviously you need the master and PCM volume levels to be high enough to hear. 
Also I use Rhythmbox and no other audio player. 
This worked for me. I hope it works for you.

---

### Post by ambishop on 2013-02-08
You need to figure out where the feedback is coming from:

From Terminal type: amixer

Results on my 12.10 imac machine below

ambishop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Bass Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 29 [94%] [9.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 30 [97%] [10.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 29 [94%] [9.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 38 [83%] [22.00dB] [on]
  Front Right: Capture 38 [83%] [22.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [off]
  Front Right: Capture 41 [89%] [25.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 45 [98%] [29.00dB] [off]
  Front Right: Capture 40 [87%] [24.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 118 [98%] [29.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'

Each audio input and output are listed.  Then one by one mute and unmute each item until the proper speakers work and microphone work without the feedback

open a second terminal window and type the following command each time changing the 'Master' to the other sources listed such as 'Capture' etc.
/usr/bin/amixer -q -c 0 sset 'Master',0 mute

and to unmute use
/usr/bin/amixer -q -c 0 sset 'Master',0 unmute 

I recommend using pulseaudio or other volume control to unmute each one as you determine which has the issue

Each time you will change the audio input or output by changing the corresponding source listed in the amixer command

/usr/bin/amixer -q -c 0 sset 'Capture',0 unmute

eventually you will be able to determine where the feedback is coming from and determine which audio inputs and outputs work best for you without getting feedback.  for me, I turned off Master, Capture, Mic Boost and Input Source and then from PulseAudio Volume Control I unmuted Master and Mic and my feedback was gone.  I suspect my issue was with Mic Boost, which is the likely cause

---

