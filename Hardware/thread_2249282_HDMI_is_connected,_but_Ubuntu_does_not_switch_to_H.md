---
title: "HDMI is connected, but Ubuntu does not switch to HDMI Audio by default"
date: 2014-10-20
forum: Hardware
---

### Post by sjeon on 2014-10-20
**OS & Hardware**
Asus Q200E Laptop
Samsung 32" UN32EH4003 HDTV
Ubuntu 14.04 LTS 64bit

**Problem (And storytime)**
Starting up Ubuntu via Live USB, tried to play audio. I could hear it ever so faintly, so I turned up the volume. Slightly better, but still something was clearly wrong. Came closer to the devices and realized that the audio is actually coming out of the laptop instead of the HDTV. Weird. Okay. So, I sought ought the setting for switching to HDMI as the output device, and OH BOY did that work! 100% volume on Ubuntu, 100% volume on the TV. Remember, I thought it might have been the TV that wasn't loud enough about a minute previous to this. So, I rocket over to the sound control functions for my dear life as the audio is BLASTING at full volume, and then I quiet it all down and now it works fine.. Still.. It was a quite traumatic experience, I assure you.

**My solution**
Had to figure out how go to Sound Settings and click on HDMI / DisplayPort and then rapidly scurry to turn down the volume because the 100% default setting was accidentally VERY loud.

**Thoughts**
+ If HDMI is connected at boot, I think that should probably be the default audio device unless something's plugged into the speaker jack
+ When HDMI becomes plugged in, I think it should automatically switch audio to HDMI unless something's plugged into the speaker jack
+ Default HDMI volume of 100% volume was alarmingly loud in my experience

---

### Post by grahammechanical on 2014-10-21
The default volume level for any install of Ubuntu is about half way. It used to be mute but that causes problems for those with hearing difficulties. They do not know when to enter their login password.

 Piping the audio from the motherboard into a TV brings two volume controls into play. We get the sound level that we have adjusted by means of the OS volume control which is then adjusted again by the volume setting of the TV. And it is the TV that has the most powerful sound amplifier of the two pieces of electronics.

The OS cannot set the default volume for the laptop speakers to half and at the same time set the default volume for HDMI to full volume. As regards sound level it matters not at all to the OS what sound output connector we are using. The OS volume control is working with the motherboard audio electronics.

You will also find a third audio setting coming into effect when you play a video through the web browser. The sound output level from the video will be boosted by the sound level in the motherboard audio electronics and then a third time by amplifier of the TV. 

Self-inflicted wounds cannot be blamed on the developers.

Regards.

---

### Post by sotiris2 on 2014-10-21
Actually pavucontrol has different volume sliders both for different devices (and usually sound over hdmi is provided by a 'device' on the card) and even for different ports of one device: As in my laptop only has one sound device but two port options, speakers and headphones which can have independent volume levels (as in when i plug my sound system in headphones port i can have it be lower than it is for laptop speaker).

For setting a default device i suggest you take a look [here](http://askubuntu.com/questions/145135/set-default-sound-device-output) and [here](http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line).

---

