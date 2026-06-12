---
title: "Hardware woes"
date: 2019-01-29
forum: Hardware
---

### Post by kriswaatch on 2019-01-29
Hey everyone

First of all, I really hope this is the right thread that I'm posting in.

I bought a new motherboard (asus prime b450m-a), AMD Ryzen 5, 8Gb RAM setup 2 days ago. While at the computer store, I mentioned to the sales fella that I need to set up a microatx case / setup that I can setup a local web server and a media player using Ubuntu. So, he suggested the above. I also said I don't want an expensive unit, just something that will work with Ubuntu.
I just spent the last couple days installing Ubuntu 18.04, 16.04 and even just tried Manjaro, with zero success. I can only get stereo playback. I installed pulseaudio and tried fiddling with that. I even updated the bios, which locked me out of my installation. Which I then found out it was apparently because of gpt. So, I even tried doing a Rufus USB installation disk with uefi, with zero success. So, I reverted back to the previous BIOS version, and here I am again, back at square one.
I just don't get why I can get 5.1 passthrough from a raspberry pi3 and not with a full fledged computer with newer hardware. 
Can someone please help me out here. I'm thinking of returning the hardware I bought and either asking for my cash back, or upgrading. And if upgrading is an option, can anyone here recommend a microatx mb and cpu?
Rant over...sorry :(

Thank you

---

### Post by mastablasta on 2019-01-30
Looking on the web it seem the motherboard is not praised for it's linux compatibility

[https://forums.linuxmint.com/viewtopic.php?t=245987](https://forums.linuxmint.com/viewtopic.php?t=245987)

some people had even more issues some had less.

[https://www.phoronix.com/scan.php?page=news_item&px=ASUS-Linux-Mobo-List](https://www.phoronix.com/scan.php?page=news_item&px=ASUS-Linux-Mobo-List)

also i am not sure what your issue really is. is it OS install & boot or just sound?

---

### Post by kriswaatch on 2019-01-30
Hey mastablasta

thanks for the reply.

Long story short, the mb has a spdif out and hdmi. I'm plugged in via hdmi (I want 5.1). With my raspberry pi, I was getting 5.1 passthrough.
In pulseaudio, it's showing 2 cards, the hdmi card and the spdif out. The spdif out is showing that it is capable of producing ac3, dts and whatnot, yet, the hdmi is only showing that stereo is available. This makes no sense.
In also, again, I have two choices, hdmi and spdif. the spdif again is showing the capability to have 2, 4 or 6 channels, yet the hdmi, I can't even raise the volume, change the number of speakers, nada, nothing. 
Last night, I installed 16.04, upgraded via ukuu to the latest kernel. With no success. In additional drivers, I see nothing. It's just absolutely baffling.
I'm thinking of returning the mb and cpu and getting something else. Can anyone suggest something else, without breaking the bank, a microatx mb?

---

### Post by Autodave on 2019-01-30
You're not running an Nvidia card in that, are you?

---

### Post by mastablasta on 2019-01-31
ok sound issues then. this depends on the sound chip and availability of drivers as well as implementation of them.

typing alsamixer in cli will open mixer that will show a bit more options. sometimes certain channels are muted in the background.

in any case you need to find out what the sound chip (e.g. from tech documentation) is and how is it recognised by the OS.

---

