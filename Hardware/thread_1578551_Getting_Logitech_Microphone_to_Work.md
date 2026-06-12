---
title: "Getting Logitech Microphone to Work"
date: 2010-09-20
forum: Hardware
---

### Post by corrytonapple on 2010-09-20
I have a Logitech microphone that I can not get to work. How would I get it to work? It is not USB, and I have already gone to Sound Preferences. I have all drivers installed, and it is an external microphone. Also it Sound Preference, it shows it is getting no input at all. Can I have some Help getting thing to work? I am running the Ubuntu 10.04, with a simple input and output on the front of the machine. I am trying to use the OSS (Open Sound System), since ALSA is not working. I think the sound is a Intel HR9 or something like that. It is a Toshiba l455-S5008.

---

### Post by efflandt on 2010-09-21
Sometimes what the plugs do depends upon your sound settings.  For example normally under your Sound Preferences, Hardware it might show Internal Audio, 1 Output/1 Input, Analog Stereo Duplex.

If it shows something different like more speakers for surround sound, sometimes the Mic socket might actually be used for one of the other sound "output" channels instead of "input".

Or it is possible that your PC has more than one Mic socket.  Under Sound Preferences, Input, Connections: the drop down list for mine shows Microphone 1, Microphone 2, and Line-in.  So you might need to figure out which is front or rear jack and make sure that you are not using a Line-in jack, which would be for a pre-amplified source not a microphone.

Does the microphone work in any other OS on any computer?

---

### Post by corrytonapple on 2010-09-28
Thank you for the reply. I am sorry for the late reply, school has been overwhelming. I recently switched to the OSS (Open Sound System) and it detects no input. I also should and will add that this is a laptop, with a input and output on the front of the system. I will look again, but that I recall it had nothing to show.

---

