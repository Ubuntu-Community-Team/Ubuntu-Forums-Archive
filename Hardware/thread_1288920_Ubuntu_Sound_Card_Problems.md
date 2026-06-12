---
title: "Ubuntu Sound Card Problems"
date: 2009-10-11
forum: Hardware
---

### Post by yunusabd on 2009-10-11
[B]I found this post here [http://ubuntuforums.org/showthread.php?t=630511](http://ubuntuforums.org/showthread.php?t=630511) and could not add a reply I reposted it here because I am having the exact same problem except I only have an on board sound card. 

Thank You
[/B]Ubuntu Sound Card Problems!!!             
                                                                I have an interesting situation with going on with my Ubuntu computer. I have the latest version of Ubuntu installed. I have 2 sound cards on my computer: one that is attached to my motherboard and a much nicer PCI one (some kind of Audiology ZS2 or something like that) I have all of my speakers connected to the PCI card. Sometimes, at random, when I boot up my computer, I’ll have no sound at all – nothing. Sometimes I can reboot it and the sound will come back. Sometimes it doesn’t. Someone suggested that I disable the motherboard’s sound card in the system BIOS and that might solve the problem. Does anyone know what’s going on or can suggest a quick fix for this? Keep in mind I’m fairly new to the Linux desktop.

Thanks!

Jason


                                  **Re: Ubuntu Sound Card Problems!!!**             
                                                                   That poor computer of yours must be getting terribly confused about which sound device to load.

Go into the BIOS and disable your on-board sound chip. That way your computer will use the Creative Audigy sound card (much better sound output).

Don't forget to plug your speakers into the card outputs.

---

### Post by Dark_Stang on 2009-10-12
Not sure about disabling onboard sound...that will vary from motherboard to motherboard, if it's even an option for your board. But you should be able to go System > Preferences > Sound. And there you will see your default playback device. Make sure it's set to the PCI card and you should be good.

---

