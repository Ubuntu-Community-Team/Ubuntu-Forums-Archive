---
title: "Strange webcam and microphone craziness"
date: 2010-03-07
forum: Hardware
---

### Post by Stev0 on 2010-03-07
Here's a strange problem if anyone can figure it out. Using a Gateway NV53 laptop with Ubuntu 9.10. Thing works perfectly in almost every aspect, the only problem I have is this: Sound works fine in everyway, using pulse audio, output perfect, built-in microphone perfect, all sound is clear as can be. However, when I attempt to utilize a program that uses both the built-in mic and the webcam, IE like Skype or empathy, suddenly all sound input stops. Webcam is clear, sound output continues as normal, however the sound input ceases, and it requires a restart in order to get the sound input working again.

I've searched the forums and google, can't seem to find any instances of other folks having a similar problem. Obviously its some kind of conflict between the two devices, and I'm assuming it has something to do with gstreamer properties, but I'm not totally familiar with how it works. Any ideas?

---

### Post by mikefreeman on 2010-03-21
I know this won't help you, sorry... Have you done anything special to get the built-in microphone working? I have the same laptop, with Mint 8 (which is Ubuntu 9.10 with a few extra programs), but the microphone does not work at all, whether it is used with the webcam or not. Thanks!

---

### Post by sarmadzhiev on 2010-05-18
> **mikefreeman said:**
> I know this won't help you, sorry... Have you done anything special to get the built-in microphone working? I have the same laptop, with Mint 8 (which is Ubuntu 9.10 with a few extra programs), but the microphone does not work at all, whether it is used with the webcam or not. Thanks!

This bug seems to be plague all hda SBx00 microphones
I saw a bug 480815 and the user gilianphilippo had a working solution. I have tweak it a little and tested it works on NV53

Add following 
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
to /etc/modprobe.d/alsa-base.conf

---

### Post by acron1 on 2010-05-18
> **sarmadzhiev said:**
> This bug seems to be plague all hda SBx00 microphones
I saw a bug 480815 and the user gilianphilippo had a working solution. I have tweak it a little and tested it works on NV53

Add following 
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
to /etc/modprobe.d/alsa-base.conf

The above solution worked like a charm on my Toshiba Satellite T115D-S1125... now, I am happy to report that as far as I know everything works as it should on this laptop-netbook... Thanks

---

