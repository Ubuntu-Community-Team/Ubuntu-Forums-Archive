---
title: "No Sound Xubuntu"
date: 2016-02-15
forum: Hardware
---

### Post by doug33 on 2016-02-15
Greetings,

This is my first post here. I have spent time on Google trying to solve this problem with no luck. I am a long time DOS/Windows user. I have been using Puppy Linux for a few years on older computers. My terminal expertise is limited, but I will type in whatever I need to.

I bought this computer from FREEGEEK a couple of days ago and the sound has not been working in xubuntu since I got it. 
Right now I am using the onboard sound card which is ENABLED in the BIOS. I booted up with Puppy Linux Live CD and the sound worked fine.

So here are my sound issues
1. onboard sound not working.
2. I installed a SoundBlaster Live CT4830 which I would like to get working, but I would like to resolve the onboard sound first.

Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

Thanks for any help,
Doug

---

### Post by ajgreeny on 2016-02-15
The xubuntu version 12.04 is no longer supported, though it is possible that you may still be getting updates of the ubuntu background parts of the OS.  You should really upgrade to a supported version, which at the moment would be either 15.10, which is supported till next July, or my choice of 14.04, supported till April 2017.

As for the sound, you can try to open Sound Settings from the volume icon in the panel and make sure the hardware is appropriately selected, and the volume settings are correct.

I can not help with soundblaster hardware as I use only onboard sound hardware.

---

### Post by Dennis N on 2016-02-15
Xubuntu 12.04 > Menu > Multimedia > Pulse Audio Volume Control

Check the volume control settings while playing a music file in the music player. There are several mute volume locations. Playback tab should show activity for your player in the lower half if it is working and not muted on this tab. Output tab should show activity if not muted on this tab. Configuration Profile should be Built-in audio > Analog Stereo Duplex. The player itself also has a mute volume.

Check alsamixer in terminal to be sure the levels on Master and PCM are not at zero. Adjust these with arrow keys.

---

### Post by doug33 on 2016-02-15
Little strange,  I changed it to **Analog Stereo Duplex** and was able to listen to a CD, then I stopped the CD and took it out and now I am **not** getting sound. I will shut it down and check it out tomorrow and let you know what happens.

Thanks for the help

---

### Post by Bucky Ball on 2016-02-15
As mentioned, Xubuntu 12.04 LTS not supported. Expect more issues as time goes by and I would take the machine off the net as it will become more vulnerable to attack as time goes by (you haven't had security updates, or any significant updates, for nearly a year). 

Post a new thread is you have issues with a supported release. Good luck.

---

