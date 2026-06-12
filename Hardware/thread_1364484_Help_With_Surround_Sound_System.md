---
title: "Help With Surround Sound System"
date: 2009-12-25
forum: Hardware
---

### Post by Zayfox on 2009-12-25
So, Christmas day came, and among other things I got a 5.1 surround sound system. All is good, except I don't have a sound card to support it. So I buy one.

** Surround Sound System:** Logitech X-540
**Sound Card:** Unknown brand, "3D Sound card <Full Duplex 32-bit PCI BUS master, Integrated SRS 3D Sound Technology>"[B]
Ubuntu:[/B] Karmic Koala 9.10 with most recent updates as of a few days ago.

So the sound card is in the computer case, put in perfectly. However Ubuntu doesn't even pick it up, and when I plug the set into it, I don't get any sound through it, however my on-board sound works.

I need to get this working. The surround sound system wasn't cheap and I can't take it back as I got it imported from overseas, any help is appreciated.

Please don't tell me to "Search the forums" either. Done that, I found nothing.

**Edit:** I don't have Pulseaudio installed I don't think. I removed it in the process of getting a number of WiNE games working.

---

### Post by HappyFeet on 2009-12-25
First disable the onboard sound in the BIOS.

Next time you buy hardware, you might want to research ahead of time to find out what is compatible.

---

### Post by Zayfox on 2009-12-25
> **HappyFeet said:**
> First disable the onboard sound in the BIOS.

Next time you buy hardware, you might want to research ahead of time to find out what is compatible.
Disabling the onboard sound in the BIOS leaves even gnome-alsamixer picking up absolutely nothing.

As I already stated, it was for Christmas, I didn't know what model/brand I was getting, thank you.

---

### Post by bshosey on 2009-12-25
Defenantly try to disable the on board sound and see if it finds it then. Now I will say this. I do run a system with onboard sound and 2 USB sound cards and a wireless head set that looks like a sound card to ubuntu so basically running 4 sound cards.

---

### Post by Zayfox on 2009-12-25
> **bshosey said:**
> Defenantly try to disable the on board sound and see if it finds it then. Now I will say this. I do run a system with onboard sound and 2 USB sound cards and a wireless head set that looks like a sound card to ubuntu so basically running 4 sound cards.
In my BIOS, it doesn't have a blatant 'disable onboard sound' option, the only one I can find is 'Onboard Audio Controller [Enable/Disable]'. As I said, disabling this leaves me with nothing, I've checked with a benchmark tool when I disabled this and there was no audio devices whatsoever.

---

### Post by steveneddy on 2009-12-26
Exchanging your new sound card for a sound card on this page will start the process of getting surround sound on your system:

[http://tldp.org/HOWTO/Sound-HOWTO/x96.html](http://tldp.org/HOWTO/Sound-HOWTO/x96.html)

I also suspect that you will need to blacklist the onboard sound device and activate the newer sound card:

[http://ubuntuforums.org/showthread.php?t=629391](http://ubuntuforums.org/showthread.php?t=629391)

Hope this helps.

Good luck.

---

### Post by Zayfox on 2009-12-26
> **steveneddy said:**
> Exchanging your new sound card for a sound card on this page will start the process of getting surround sound on your system:

[http://tldp.org/HOWTO/Sound-HOWTO/x96.html](http://tldp.org/HOWTO/Sound-HOWTO/x96.html)

I also suspect that you will need to blacklist the onboard sound device and activate the newer sound card:

[http://ubuntuforums.org/showthread.php?t=629391](http://ubuntuforums.org/showthread.php?t=629391)

Hope this helps.

Good luck.
Thanks, I was directed to the Alsaproject site and it looks like I may well need to compile the latest ALSA drivers. However I'll probably need to blacklist my old onboard card too. I'll get back on this when I've finished.

---

### Post by steveneddy on 2009-12-26
> **Zayfox said:**
> Thanks, I was directed to the Alsaproject site and it looks like I may well need to compile the latest ALSA drivers. However I'll probably need to blacklist my old onboard card too. I'll get back on this when I've finished.

Personally I think it would be easier to just go get a supported card, but if you insist, compile away.

---

### Post by Zayfox on 2009-12-26
I've just noticed that even the alsaconf tool doesn't even pick my card up.
Verdict: Sound card issue?

---

### Post by steveneddy on 2009-12-26
> **Zayfox said:**
> I've just noticed that even the alsaconf tool doesn't even pick my card up.
Verdict: Sound card issue?

We could assume that since you stated that the audio card was a "white box" item and we can't seem to determine the brand name, chipset or manufacturer, I would simply return the new card and purchase a known supported sound card and go about the task of blacklisting onboard sound.

Give this a day of hanging in the forums because someone else might have a better idea, but this sounds like the easiest way go get to the end of your quest for surround sound from your Linux box.

---

### Post by Zayfox on 2009-12-26
The box came with Windows drivers, I simply got the model number from these and recompiled the (new) ALSA drivers with that model in the configuration
Solved, thanks for all your help.

---

