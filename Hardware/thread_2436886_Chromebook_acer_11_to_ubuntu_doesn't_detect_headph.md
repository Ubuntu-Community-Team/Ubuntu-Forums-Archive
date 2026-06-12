---
title: "Chromebook acer 11 to ubuntu doesn't detect headphones but plays sound through HDMI"
date: 2020-02-14
forum: Hardware
---

### Post by lmilol on 2020-02-14
I decided to install ubuntu 19.04 onto my chromebook acer 11, and did so without any problems. However now that I'm trying to listen to audio from my device, it only plays if I connect it to my monitor via HDMI. The internal speakers and headphone jack don't even show up on the audio device list in the settings. I have re-installed Alsamixer and Pulseaudio many times with no change in result, and have also tried to see if headphones were on mute, however I can't even do that as my headphones aren't detected.

---

### Post by oldrocker99 on 2020-02-15
The component in laptops which fails first is likely to be the headphone jack; it's happened to me. There are cheap USB sound devices which have sturdy jacks, which is the best solution for you.

---

### Post by tea for one on 2020-02-16
Is your Chromebook listed in this chart?  [https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility)

Gallium OS is built on top of Xubuntu and is designed for various Chromebooks.

I don't have a Chromebook so I am only trying to provide alternative info.

---

### Post by TheFu on 2020-02-16
ubuntu 19.04 support ended last month.
Passed time to move to 19.10.  Not worth troubleshooting on an EOL release.

As for getting things working on any chromebooks, there are websites specific to each model with guides.  Following those instructions is usually about 30 minutes to happiness.  I've done this with Acer C720 and Toshiba CB35 chromebooks.  Chromebooks are just different enough that sometimes general answers for normal laptops don't work.

Google found this: [https://askubuntu.com/questions/706447/ubuntu-running-on-a-acer-chromebook-does-not-detect-standard-audio-output-but-d](https://askubuntu.com/questions/706447/ubuntu-running-on-a-acer-chromebook-does-not-detect-standard-audio-output-but-d)

---

### Post by Mcdowellmountains on 2020-05-25
this worked  for me, check it out.

[https://github.com/yusefnapora/pixelbook-linux](https://github.com/yusefnapora/pixelbook-linux)

---

