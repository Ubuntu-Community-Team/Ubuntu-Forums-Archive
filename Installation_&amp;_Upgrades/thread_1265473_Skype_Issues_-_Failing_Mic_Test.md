---
title: "Skype Issues - Failing Mic Test"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by chome4 on 2009-09-13
Installed Skype and during the mic test, I get major hissing during playback!

Medibuntu is installed.

Under Options, all settings, Microphone, Speakers and Ringing are set to 'PulseAudio server (local)'

What do I need to do to stop the hissing?

Using Skype (Beta) Version 2.1.0.47

---

### Post by rvlaurita on 2009-09-15
Having the same problem.  I tried changing the microphone settings but that did not fix the problem.

---

### Post by danjscott on 2009-09-21
Same problem here - I have it working fine on Fedora and Eeeubuntu, but loud hissing on plain Ubuntu.

---

### Post by mionescu on 2009-09-23
This might be a known problem for the current beta version of Skype (2.1.047). See
[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)
the second question (about clicking noise) for a possible solution. If it does not work I will advice you to install Skype 2.0 (stable) from medibuntu.

---

### Post by alexmoon on 2010-01-20
Thanks for the help so far. I tried following the instructions [here]("http://share.skype.com/sites/linux/2009/09/some_explanations.html") and changed autospawn to "no" but it doesn't seem to have helped. The list of audio devices still only had pulse listed.

 I have tried following [the instructions]("https://help.ubuntu.com/community/Medibuntu") for installing Medibuntu, but now I can't work out how to install Skype 2.0... it is not showing up in 'add/remove applications' skype isn't listed in [Jaunty's list of Medibuntu packages]("http://packages.medibuntu.org/jaunty/index.html"). 

Any advice on how to install Skype 2.0 or how to get sound working on the newer beta version?

---

### Post by mionescu on 2010-01-20
Skype 2.1 (beta) works great on Karmic. I updated my computers to Karmic and the sound is working just great. This would be my best advice.

I don't know why did Medibuntu pull out Skype from their repositories. I noticed that this is the case for Karmic as well.

---

### Post by alexmoon on 2010-01-20
Unfortunately my last few attempts to upgrade led to pretty severe problems, so I'm nervous about trying again. Is there anything else I could try?

---

### Post by mionescu on 2010-01-20
I noticed that Skype just released a new beta for Linux. It is version 2.1.0.81. Try to install it and see if it works. You can download it from the Skype official website: [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

Try to install also "pavucontrol" (using Synaptic) and run it. I use this tool to select the recording device and other fine tuning for pulseaudio.

---

### Post by alexmoon on 2010-01-20
Hurrah! The new version of Skype fixed it! I haven't tried pavucontrol, but may fiddle with it later as well. Thank you.

---

### Post by manoj1987 on 2010-09-11
The solution is simple.
1. Goto Sound Preferences
(System-->Preferences-->Sound)

2. In that goto "Input" tab 

3. In that you could see "Connector" option. Try each of the options and  do the skype. You would succeed in any of the selections!

4. In the same tab there is an option "Choose a device for input"
For that option, i just have one device listed: "Internal Audio Analog  Stereo"
If you have any other option, try them too and do the skype test!

---

