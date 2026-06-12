---
title: "Lifecam VX-800 microphone not working"
date: 2014-08-04
forum: Hardware
---

### Post by gep2 on 2014-08-04
Hi, I've installed Ubuntu 14 LTS on my new desktop and everything seems to work fine except for the microphone of my MS Lifecam VX-800.
I need it to use Skype.
The video works fine, but the microphone does not.
I have tried to insert an old microphone into the mic-in jack and it works fine (except that it's very very old and the sound quality is awful).
What can I do?
The VX-800 does not appear in the Input tab of the Sound Preferences program.
Similarly it does not appear in the Sound Preferences in Skype (while it explicitly appear in the Video Preferences for Skype). Skype only mention PulseAudio in the microphone drop-down box.
Any help much appreciated!

---

### Post by kostkon on 2014-08-04
Try connecting it to another USB port and then check in your sound preferences again.

According to [ this page]("https://wiki.ubuntu.com/SkypeWebCams") it should work OTB.

What's the output of these commands:
```
aplay -l
```
and
```
cat /proc/asound/cards
```

---

