---
title: "[SOLVED] Mic troubles in Skype"
date: 2008-11-13
forum: General Help
---

### Post by CNLiberal on 2008-11-13
I have a Dell Latitude E6500 laptop with built in webcam and mic.  I'm currently running x64 8.10 with all updates.  I have installed Skype.  In "Options", under "Sound Devices", I have set "Sound Out" and "Ringing" to "pulse" as that's the only option that works.  I have tried all the different options for "Sound In" and whenever I make the test call, I never hear myself.  I really have no idea where to go from here.  I've never messed around with recording from a mic on Linux.  Any help would be appreciated.  The webcam seems to work as I can see myself in the webcam test window in Skype.

As a side note, I'm also having volume issues.  When I use the volume slider in the task bar and move the slider halfway down, there is no sound coming out of the speakers.  It's as if halfway down is mute.

Thanks for the assistance!

Jim

---

### Post by CNLiberal on 2008-11-13
I got this working.  I had to fiddle with the Volume Control Applet.  Under Volume Control, Preferences, I choose "Digital Input Source".  A new tab appeared under Volume Control.  I choose "Digital MIC 1".  Then I could start recording/Skype-ing again.  I also went into my Volume Control and turned all volumes to max, and now my music plays at an appropriate volume.  It's still muting at the halfway mark, but I can open another ticket about that.

Jim

---

### Post by Aussieartist on 2008-12-18
HP dv5t inbuilt mic and cam (tested with Skype 2.0.0.72 and Ubuntu 8.10)

I have a new HP dv5t with inbuilt webcam and mic. I had some probs with getting the mic to work. Here's what I did:

Open Ubuntu Volume Control Preferences  
Check all Playback boxes except PC Beep
Check all (3) Recording boxes
Check all (3) Options boxes
Don't check any Switches boxes

Go back to Volume Control
Select HDA Intel (Alsa mixer) as device
in Options tab: select Digital Input Source as Digital Mic 1
select Input Source (upper) as Front Mic
select Input Source (Lower) as Mic
in Recording tab: unmute all and X Toggle audio recording on all
Turn up sliders on Capture to about half

go to Skype Options - Sound Control section
select HDA Intel (hw:intel,0) for sound in and sound out
If you let Skype adjust levels it seems to fluctuate in volume.
I chose to play with Capture sliders until I got a good level in the recording.
There still seems to be some fluctuation in volume, possible because it's a condenser mic?

I made test call(s) in Skype until the above combination of inputs and mics worked.
It may be weird but any other combination of the above seems to stop the mic from working!!!

Hope this makes sense... I'm new to Linux. This is my first install!

---

