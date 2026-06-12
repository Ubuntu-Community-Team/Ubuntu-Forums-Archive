---
title: "Headphones not speakers"
date: 2012-03-13
forum: Hardware
---

### Post by Winterfox on 2012-03-13
Hey, thanks for reading,

I've recently installed Ubuntu 64bit onto my HP Pavillion DV6 1210sa to replace the awfulness that was Vista 32bit.

The problem I have is that the sound works but I cannot get the speakers to mute when I plug in headphones.

I have tried to fix with the solutions I've found but either I'm doing something wrong or a file is missing for the step-by-step I follow.

Official driver from HP is IDK HD Audio Codec Driver - 6.10.6225.0 A

Does anyone now of any/can point me to a way to sort this out?

Cheers

---

### Post by wyliecoyoteuk on 2012-03-13
I had this in reverse, I wanted to run some wireless speakers in another room off the headphone jack.
If you are using ALSA, install alsamixer.
When run, select controls, one of them under "switches"should be "automute". tick this.

---

