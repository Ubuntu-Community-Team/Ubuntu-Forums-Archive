---
title: "Microphone goes all fuzzy"
date: 2009-06-22
forum: Hardware
---

### Post by Schlorgadorb on 2009-06-22
I installed Ubuntu about a week ago, and it has been completely awesome compared to my experience with Windows, all save for one problem I've been having: 

Every time I test my microphone, or try to get it working, all I get is this weird fuzzy static. Whenever I tap it, it makes a noise which then echoes as if fading to the distance. But it never records anything else. Just odd static. I tried yelling into it, blowing into it, nothing works. 

Its an on-board mic for a Vaio Laptop model VGN-AR770. The mic worked when I was using Windows, but it doesn't now. 

I've tried going into the settings and turning the volume to max, I turned off the mute on every option, I would think there would be some kind of change at least, but I get nothing. I've tried using all eight of the options for Sound Capture in Preferences, including Test Sound and Silence, which give a loud beep and nothing respectively. Using "HDA Intel ALC262 Analgo (ALSA)" I get silence as well, but with every other option, its this weird fuzzy sounding static. 

My thought is that its a problem with the drivers, but I don't know how to install drivers. If anyone else knows about this problem, could you help me out? And failing that, could someone tell me how to update drivers properly so that I don't screw it up?

---

### Post by gradinaruvasile on 2009-06-22
You should try Alsamixer (the one from the terminal). The gui-based volume control sometimes behaves differently than it should.
So, open a terminal and type:

```
alsamixer
```

It has a bit confusing interface, but once u got the hang of it u can work with it.

Top to bottom u have 4 lines : Card, Chip, View, Item. Card and chip is only informs u about your hardware.
View: 3 tabs - Playback - It has the items related to playback
                        - Here you should mute mic, cd, line because those settings may cause interference
             - Capture  - Items for sound capture (mic volumes, capture volumes)
             - All      - All items in a disorganised manner. Never used it for anything useful.

Navigation: TAB for changing the tabs, left/right changing items, up/down changing volumes/devices (such as in input source tabs changing mic1, mic2, front mic, etc), "m" mutes/unmutes items (only those that have a box right under the volume bar). Space is used to set capture devices - this works only if the item has    "-----" between the volume level and the volume bar. Set only 1 source.

---

### Post by Schlorgadorb on 2009-06-22
Well, I checked ~/$ alsamixer, and it does display a list of the capture devices. I don't know how to actually test them with alsamixer, so I used the preferences test button, and I got the same result, although this time it seems there's a pause before the static starts. I don't know if that means anything.

I tried setting each device individually on, and tested each device in the preferences window. Nothing seems to work. 

If I were to get a USB microphone, would that include its own drivers? And if so, how would I set Ubuntu to use those drivers?

---

### Post by Schlorgadorb on 2009-06-22
Ok, I plugged in my USB headset, which previously wasn't working, tried the things mentioned here, and it worked.

However, the main purpose of my trying to figure this out is to use Teamspeak. So now that I have a working microphone, albeit not the one I was thinking of, I need to know how to set it to use the proper device. I'd still like to know why my in-built mic has this issue, but I can wait a while before solving that mystery.

As for Teamspeak, I have three options for the "Sound Driver" I have, Default (oss /dev/dsp), default network (8780:L) and Other which has a text box. 
So I guess the question would be, where is the driver for the USB headset stored?

---

### Post by killjoy123987 on 2009-06-24
I am having the same problem as you, my mic seems to capture my voice, because i can hear it through my speakers, but when i try to record or use temaspeak all I get is static and wierd noise, I have tried alsamixer but no luck.

---

