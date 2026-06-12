---
title: "Hardware for Linux-based media center?"
date: 2011-05-07
forum: Hardware
---

### Post by Sidrabs on 2011-05-07
Hello,

I am dreaming about Linux-based hardware: a compact, low-power PC that features DVD reader, network card, ideally a radio tuner card, has some kind of standard audio/video input and output, remote control, and is Linux-based.

This device would:
- take the audio/video input from digital TV tuner
- read the DVD discs, display their menus, subtitles, etc.
- capture the aired radio (I know, sounds so iron-age, but pretty reasonable wish in my area)
- be able to open web browser to navigate to some video sites like youtube
- be able to capture various Internet radio streams
- play back various video/audio files
- provide a nice media center where all that stuff can be selected, mixed etc.

Does something like that exist in the market?

---

### Post by mosquitogang201 on 2011-05-07
If you can build it yourself, yes. I'm not aware of any companies that make these AND that are completely Linux compatible.

I have one of these myself. The hardware doesn't have to be all that great, but the important parts are:

Nvidia graphics card (so you can use VDPAU hardware acceleration for videos)
TV tuner card

The tuner card is probably the toughest to pick out, because there is not a lot of info on what works or not, and if you do find it it is probably outdated. What kind of TV signals are you actually wanting to capture? If its just over the air digital or clear QAM cable, I can highly recommend the Hauppauge 1600 card, if you go that route let me know and I will find which version of it I have. I have digital and analog TV and FM radio working on it, although it can be a little finicky which switching between analog TV and FM. You can also find a tuner which will take composite or component input in from a set top box and then set up an IR blaster to control the set top box - you'd have to research to see what works.

You can buy cases that fit in with the rest of your A/V equipment as well. Newegg has an entire case section for this. You can find one that comes with the remote and receiver as well to save you a step.

Finally for software you will want to run MythTV. Highly recommend Mythbuntu since everything comes mostly set up for you.

---

### Post by tomgriffin1956 on 2011-12-26
I have just put together the hardware for my Linux-based HTPC. I would like some of the SMEs (Subject Matter Experts) on this forum to look it over and see if I need to do anything different or if I am going to run into any difficulties. I plan on using this to record OTA HDTV as well as handle other media functions.

Siverstone LC 13B-E Case
OCZ 500W ModXStream-Pro modular power supply
Gigabyte GA-X48-DS5 Motherboard
Intel Core 2 Duo 316 ghz CPU
4G Corsair DDR2 RAM
EVGA NVidia GeForce GT430 1G DDR3
Hauppauge HVR 2250
WD Caviar Blue 500 G HD
Seagate Barracuda 1TB HD

Have already prepared install disks for both Mythbuntu 10.04 and 11.04 in case of difficulties. I also have the firmware unzipped and on a thumbdrive ready to load.

I am a Linux ***_newbie_* **although I have been running Linux Mint 8 on my main home computer for the last 2 1/2 years. (Got real tired of Windows and the Gates trap) I plan on taking this fairly slow and not get my BP up too bad, so be patient with me as I don't have a lot of spare time.:D

---

