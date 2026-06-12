---
title: "Sound Stopped on Only One User"
date: 2015-08-15
forum: Hardware
---

### Post by gerowen on 2015-08-15
We have a desktop PC in the living room that is used as a media center PC with a wireless keyboard/mouse combo.  I've got separate usernames for myself (administration mostly since I use the laptop most of the time), my wife, and my son (his account has restrictions in place, game icons on the desktop, etc.).  She plugged in my Playstation Eye webcam, which we have used before on several machines including this one, in order to use it with Skype.  When she did, the sound output stopped, and won't come back.  The sound works fine on all the other user accounts, and the audio device is listed correctly under the sound controls as well as pavucontrol, and pavucontrol shows that sound is being sent to the card with the little animated signal meters, but nothing actually gets played.  I've tried switching the audio cable from the digital out to the regular headphone out and still no audio, but still, it works just fine on my user account and my son's.  The microphone in the Playstation Eye works just fine because I can use "OK Google" in Google Chrome.  I've tried unplugging the camera and rebooting, I've tried manually reloading alsa and pulseaudio, and rebooting the entire computer.

The computer is running Ubuntu 15.04.

---

### Post by gerowen on 2015-08-15
Fixed it, I just deleted the ~/.config/pulse folder and rebooted.

---

