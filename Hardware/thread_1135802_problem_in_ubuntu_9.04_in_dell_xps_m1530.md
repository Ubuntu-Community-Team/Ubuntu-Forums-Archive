---
title: "problem in ubuntu 9.04 in dell xps m1530"
date: 2009-04-24
forum: Hardware
---

### Post by Gladiator-prog4me on 2009-04-24
hello 

i have installed ubuntu 9.04 for notebook in my laptop dell xps m1530 

but the sound audio and mic  is low 

please help me to fix this problem 

thank you

---

### Post by Gladiator-prog4me on 2009-04-24
up

---

### Post by damis648 on 2009-04-24
Please, only bump every 24-48 hours.

Go to the sound settings (Click Panel Applet > Volume Control) and in Edit > Preferences enable all the channels. Back in the volume settings, turn everything up. Try playing something now. :popcorn:

---

### Post by Gladiator-prog4me on 2009-04-24
> **damis648 said:**
> Please, only bump every 24-48 hours.

Go to the sound settings (Click Panel Applet > Volume Control) and in Edit > Preferences enable all the channels. Back in the volume settings, turn everything up. Try playing something now. :popcorn:

i have do that , but the sound still low !

---

### Post by jespdj on 2009-04-24
This is a known bug which affects a lot of people:
[https://bugs.launchpad.net/bugs/275998](https://bugs.launchpad.net/bugs/275998)

---

### Post by Gladiator-prog4me on 2009-04-24
> **jespdj said:**
> This is a known bug which affects a lot of people:
[https://bugs.launchpad.net/bugs/275998](https://bugs.launchpad.net/bugs/275998)

i'am sorry sir i can't understand any think from this site , 

so can you tell me step by step how i can fix the problem ? 

thank you

---

### Post by Gladiator-prog4me on 2009-04-26
up

---

### Post by libralibra on 2009-04-26
hey, dude, try this command within terminal:
```
alsamixer
```

Then use F5-key to adjust the volume

Enjoy!

---

### Post by Gladiator-prog4me on 2009-04-26
> **libralibra said:**
> hey, dude, try this command within terminal:
```
alsamixer
```

Then use F5-key to adjust the volume

Enjoy!

thank you sir , i will try it now

---

### Post by Gladiator-prog4me on 2009-04-26
hello 

i have do that , but the sound still low !

---

### Post by Gladiator-prog4me on 2009-04-26
and mic is not working !

---

### Post by Gladiator-prog4me on 2009-04-27
up :(

mic is down !! not working 

please help me

---

### Post by Gladiator-prog4me on 2009-04-29
please help me !!!!  

i still wait 3 day and more  !

---

### Post by jespdj on 2009-04-29
Please remember that the people in the forums here are all volunteers, helping others because they like Ubuntu and want people to be satisfied with it. Nobody here is under any obligation, so you cannot demand an answer. Crying, doing nothing yourself and complaining is not going to solve your problem. A negative attitude is not going to make people want to help you.

I already pointed you to the [bug report](https://bugs.launchpad.net/bugs/275998), but you're not willing to read through it. The comments contain some workarounds for the problem.

So, you just want a simple and quick fix. Ok, I'm going to tell you step by step how I fixed the problem on my XPS M1530.

First, go the the Ubuntu volume control: Click the speaker icon in the top right of the screen and click the "Volume Control..." button. In the volume control, click Preferences at the bottom. In the list of things to be made visible, make sure that "Capture" and "Digital Input Source" are checked. Close the Preferences window. Go to the Options tab. Make sure that it says "Digital Input Source: Digital Mic 1". Go to the Recording tab. Set the volume of "Capture" to the max. setting. Close the volume control.

Then, you need to install **pavucontrol**. Install that package with Synaptic, or via a terminal command:
```
sudo apt-get install pavucontrol
```
Then go to the PulseAudio manager by entering the command:
```
paman
```
In the PulseAudio manager, go to the Devices tab and select the "alsa_input" device (see first screenshot) and click Properties. Set the volume to about **135%** (see second screenshot).

Now the microphone should work. You can test it with Sound Recorder (Applications > Sound & Video).

---

### Post by Gladiator-prog4me on 2009-05-01
> **jespdj said:**
> Please remember that the people in the forums here are all volunteers, helping others because they like Ubuntu and want people to be satisfied with it. Nobody here is under any obligation, so you cannot demand an answer. Crying, doing nothing yourself and complaining is not going to solve your problem. A negative attitude is not going to make people want to help you.

I already pointed you to the [bug report](https://bugs.launchpad.net/bugs/275998), but you're not willing to read through it. The comments contain some workarounds for the problem.

So, you just want a simple and quick fix. Ok, I'm going to tell you step by step how I fixed the problem on my XPS M1530.

First, go the the Ubuntu volume control: Click the speaker icon in the top right of the screen and click the "Volume Control..." button. In the volume control, click Preferences at the bottom. In the list of things to be made visible, make sure that "Capture" and "Digital Input Source" are checked. Close the Preferences window. Go to the Options tab. Make sure that it says "Digital Input Source: Digital Mic 1". Go to the Recording tab. Set the volume of "Capture" to the max. setting. Close the volume control.

Then, you need to install **pavucontrol**. Install that package with Synaptic, or via a terminal command:
```
sudo apt-get install pavucontrol
```
Then go to the PulseAudio manager by entering the command:
```
paman
```
In the PulseAudio manager, go to the Devices tab and select the "alsa_input" device (see first screenshot) and click Properties. Set the volume to about **135%** (see second screenshot).

Now the microphone should work. You can test it with Sound Recorder (Applications > Sound & Video).

thank you 
thank you 
thank you 

finally the microphone is working fine , 

have a nice day

---

### Post by IraGainesUK on 2009-06-26
Sorry for bringing up a slightly old post but I just had to say thanks very much to jespdj for solving my long-running problem with the microphone (and consequently skype!)

Your instructions worked like a charm for my Dell XPS M1530 too, much appreciated.

---

