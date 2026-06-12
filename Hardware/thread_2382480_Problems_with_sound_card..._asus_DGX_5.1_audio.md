---
title: "Problems with sound card... asus DGX 5.1 audio"
date: 2018-01-13
forum: Hardware
---

### Post by Nomad Dome on 2018-01-13
Box:
Gateway sx2110G
AMD E1-1500
GeForce GT 720 PCIe
Ubuntu 17.10 64bit
Gnome 3.26.2


I had 5.1 audio support in Windows, but was not able to get this working in Ubuntu.  I tried advice on many forums with no luck.  It's possible I've mucked up some settings in that struggle.   I gave up and purchased an Asus Xonar DGX.

I am connected to a Logitech 5.1 system.  Green to green, pink to pink and black to black.

When I connect to the Logitech via Bluetooth from my phone, all 5 speakers work, so I know they are all wired correctly.

When I test my Ubuntu machine through youtube 5.1 audio test video such as: [https://www.youtube.com/watch?v=PqVCPE8_ntE](https://www.youtube.com/watch?v=PqVCPE8_ntE) , there is no sound from LFE, and all other speakers seem to give equal output regardless of which speaker is supposed to be tested.  Rear Channel speakers seem to be louder.


Sound Settings show this as:
Analog Output-CM18788 (Oxygen HD Audio)
I have selected Analog Surround 5.1 Output

Speaker test only "front right" and "front left" make any sound.   When I hit either FR or FL, the test is played equally through my two rear right and left speakers for each test.

Alsamixer v1.1.3 shows Xonar DGX CMI8786
I switched Analog output to multichannel
Stereo upmixing is front + surround

It doesn't show the channels that I would expect (master, front, surround, center, LFE)
instead, it shows Headphone,  Analog Input, Digital input 

It's like ALSAMIXER thinks this is a stereo headphone?

I'm not sure what to try next.   I appreciate any help.

---

### Post by Nomad Dome on 2018-01-14
I only use this system for streaming movies, so wouldn't be too big of a problem to reinstall Ubuntu and the few programs I've added, but I would rather learn how to fix it.

... also, is this behavior a known issue with the Asus card?  Would reinstalling Ubuntu even help?

---

### Post by Nomad Dome on 2018-01-14
Just tried with a digital optical audio cable... no joy.

Anyone have suggestions?  Please?

---

