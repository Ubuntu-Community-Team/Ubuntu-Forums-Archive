---
title: "Ubuntu recognizes disabled onboard audio???"
date: 2009-12-09
forum: Hardware
---

### Post by eckz59 on 2009-12-09
I'm running the latest stable version of Ubuntu (9.10) live on a USB key, and I essentially want to test my Sabrent TV/FM Radio tuner card SBT-TVFM. This card works fine in Windows just by using the automatic updates. I read articles suggesting how to remove the saa7134 module and reload it with the correct card and tuner options to get it working in Ubuntu. And I get video, which is great!

The problem is, I got not audio at all. The audio from the TV card gets passed to the Mic-In on my sound card and I want it to play. So I know from hooking up my DJ equipment to the Line-In of my Soundblaster Audigy 2 ZS in earlier versions of Ubuntu that I need to make sure the Mic-In is not muted.

So, I went to the sound preferences in 9.10 and I don't see the option to do this for my soundcard. I only see two Input and Output devices, both labeled Internal Audio. Sometimes I pick one output device, and the sound plays through my Audigy 2 ZS. But then sometimes it won't work unless I pick the other even though my speakers are still hooked up to the Audigy. I wanted to use alsamixer in the console, because that has previously helped me get things working correctly.

So I load up alsamixer, only instead of my Audigy 2 ZS being the card to adjust, I get my onboard soundchip. How the heck is this possible, I disabled the AC'97 Audio in my BIOS. How can linux still pick it up and set it as the default? This is making things very difficult for me; what can I do to fix this problem? So that Ubuntu realizes I have the onboard sound disabled in BIOS? Just for reference Windows doesn't recognize the onboard audio

Also I am using an ASUS K8V-SE Deluxe motherboard

Thanks for your help!

---

