---
title: "[SOLVED] 15.04 64bit Amd APU A8-5600K Unable to set analog audio to 6ch (5.1)"
date: 2016-01-16
forum: Hardware
---

### Post by SR_ELPIRATA on 2016-01-16
I've had this problem for weeks, after each and every install of a new version of ubuntu, would have to search thru google and these forums to find a way to make it so that I could change from 2 channels (stereo) to 6 channels (5.1) for my HTPC. I tried many things but none made it work. Now, keep in mind that the sound was working, I only had 2 channels available from the sound preferences (or using pavucontrol).

elpirata@Phoenix-SSD:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

What finally worked was so simple Im still speechless on why I could not find something suggesting this on the help.ubuntu.com site (under the sound section).

I had opened many times the alsamixer before, and noticed all the volume and channel volumes were set correctly, but I didnt noticed there's an option for channel, which was of course set to 2 channels.

So I went to the alsamixer using the terminal ("alsamixer") and then F6 to select audio card, use the arrows to move down to the analog audio option and hit enter. Then, alsamixer shows all the mixers and moving towards the right side, you will see the channels option, and with the up/down arrows you change that to 6 channels, and then ESC to exit the alsamixer.

To save the settings just type in terminal "sudo alsactl store" and then I restarted the system (not sure if needed though).

Next time I went into sound preferences, this time in the built-in analog sound.. I could choose between stereo and different multi channel options. Upon selecting 5.1analog audio, I went into Test Speakers, and voila! I could hear sound from all the speakers. Now, if only I could set the LFE (subwoofer) to only output sound below 60hz I would be extremely happy, but as it is, its great :)

I hope this also helps other HTPC builders using Amd APU's... but I do realize I am perhaps one of the few who still set up their HTPC's to use analog audio instead of HDMI.

---

### Post by mörgæs on 2016-01-17
Thanks for posting.
If you use Thread Tools for marking a thread solved there is a better chance that someone will find it.

---

### Post by Bucky Ball on 2016-01-17
Tis a pity you've only just fixed this as the bad news is 15.04 has about two weeks of support remaining at which time, that's right, you'll need to upgrade to 15.10.

Sounds like you'd be better off with a long-term support release. 15.10 upgrades to 16.04 LTS later in the year and that is supported for five years until 2021. Good luck.

And yes, see link in my signature for how to mark the thread as solved. Thanks.

---

