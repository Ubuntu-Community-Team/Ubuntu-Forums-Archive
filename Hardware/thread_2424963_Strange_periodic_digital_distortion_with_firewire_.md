---
title: "Strange periodic digital distortion with firewire audio interface playback"
date: 2019-08-18
forum: Hardware
---

### Post by zurn2 on 2019-08-18
Hi everyone, 

I'm having a rather peculiar issue with the playback on my io device. Basically, every minute or so the sound becomes laced with a harsh digital
distortion for a few seconds (between 3 and 10). It's easier heard than explained, so I've posted a sample of the sound here: 

[https://clyp.it/lenaagxi](https://clyp.it/lenaagxi)

I'm using a Mackie Onyx 1620i with a 003 serial number. My computer is a Lenovo X230 Thinkpad with Ubuntu Studio 18.04 LTE. The two are connected via firewire. 
It's important to note that my laptop doesn't have a dedicated firewire port - I'm using a removable 2 port fire wire card on my express port (a 2 Port 
ExpressCard 1394a from StarTech.com). Though I'm usually only using the Mackie with Ardour 5, it also occurs in other applications. 

The issue only occurs when outputting audio from the Thinkpad to the Mackie. There's absolutely no issues with recording audio to the laptop. Though I've had
some issues with the Mackie with other Ubuntu Studio kerels, it's currently working without any drivers in virtually every application, and automagically 
connects to JACK when I plug it in. There have been a few rare occassions when the issue doesn't occur at all. 

Finally, so far this problem occurs with this system only. I frequently use the Mackie with a Macbook Pro and a Mac Mini (through a Firewire to Thunderbolt
adaptor, no less) and there's never been any problem with the playback. 

Troubleshooting things I've tried:
- Both firewire ports on the ExpressPort card
- Both ports on the Mackie
- Different firewire cables
- Both Ubuntu studio kernels (low latancy and regular)
- Both ALSA and JACK drivers

If anyone has encountered an issue like this or has any leads, I'd love to hear them.

---

