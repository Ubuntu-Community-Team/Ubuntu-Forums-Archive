---
title: "ALC880 Mic does not work (Hardy, ALSA 1.0.16)"
date: 2008-04-24
forum: Hardware
---

### Post by rocksocke on 2008-04-24
Hi everybody!

i have a laptop ( Fujitsu Siemens Amilo Pi 1536 ) and tryed nearly everything to bring the internal (or pluggable) micro to record. But i have no success. It uses the hda-intel and ALC880-codec.

I compiled the newest alsa-driver (libs, utils..), played hours with the audio-settings, but still had no success.

i googled an read thousands of threads of blogs or forums and found so different things that i now am unsure if this will work anytime..

**But:** All this allthough all the tests in audio-settings work! so i don't get any errors klicking on "Test" near audio-capture.

i know this topic is around a while, but please, did anybody of you got this damn mic to work???

---

### Post by bigmäc on 2008-05-16
yep, i had the same problem with my acer aspire 5720. when i plugged in an external microphone it worked.

---

### Post by SvenBuntu on 2008-05-18
First of all I'm happy to see your post only because I know I'm not going crazy (ok I know it's not mutually exclusive). 

I have the laptop Fujitsu-Siemens Pi1536 and have put down hours ~10 to get the internal or external mic working, unfourtunately without success. Even stranger is that I found documentation for the alsamixer stating the "model=fujitsu" in alsa-base was referring to this particular moder (Pi1536). I too installed the .16 version of alsa but nothing. All sounds work perfectly, I can even see the little red light (SPIDF) in the headphone jack turning on and off by playing with the controls. 

I'm not a wizz on linux and running out of ideas. 

Anyone being able to help or point in right direction would be very appreciated.

---

### Post by SvenBuntu on 2008-05-18
A link to the documenation stating the model is supported:
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

Slightly ironic the model is mentioned there! Search on 1536.

---

### Post by rocksocke on 2008-05-19
i still didn't manage to get it working. in desperateness i bought an usb-headset which works plug'n'play. but thats not very mobile!

---

### Post by SvenBuntu on 2008-05-19
> **rocksocke said:**
> i still didn't manage to get it working. in desperateness i bought an usb-headset which works plug'n'play. but thats not very mobile!

Hmm, yes I'm starting to give up on this one. Could you tell me what headset you bought? It would be helpful to know it works on my machine. Are you using Skype with it? 

Cheers
Svenbuntu

---

### Post by daimadoshi85 on 2008-06-16
I have found a solution to use the internal mic!
At the end of the file /etc/modprobe.d/alsa-base write
```
options snd-hda-intel model=6stack-digout
```
then reboot.

After that you have to increase volume in MASTER, PCM, FRONT, FRONT MIC , SURROUND (nothing else, otherwise it won't work), and set input source to FRONT MIC, 8ch.

Then microphone will work, a bit low, but I can talk with skype now! 
:guitar:

---

