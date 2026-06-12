---
title: "Sound Problem in an HP dv2420la"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by ninhobomba on 2007-08-19
Hello.
My girlfriend and I recently got HP laptops and they came with Vista, so we installed Kubuntu 7.04 on both of them. Recently, her laptop has been behaving in a strange manner in what relates to the sound system. To be concrete, it becomes mute. Nothing sounds, not music, not the system warnings, nothing.

Yesterday was the first time it happened and I fiddled a bit with the sound panel on the system configurations app on the K Menu. I switched from autodetect to ALSA and back again, it didn't seem to work... i then rebooted the laptop and it magically worked again. Nevertheless, I kept noticing some unusual popping sound when playing games like Neverball or Trigger (the rally one)... But still, it worked.

Today I got a phone call from her and she is really worried because the computer has become mute once again. She says the fiddling with the sound panel has produced no results whatsoever and also that XP (it's dual boot) works fine with sound.
Her computer is an HP dv2420la, and Kubuntu didn't need any sound device drivers when we installed. I'm wondering if perhaps we need to install a special driver or something.
I'll be very grateful if anyone could help us out.

---

### Post by EXCiD3 on 2007-08-19
You could try installing the newest version of ALSA. You can just search for a Howto as there are several of them floating around... Let us know the results.

---

### Post by ninhobomba on 2007-08-21
Well, according to adept... our ALSA is pretty recent... but i don't know if there is a better way to check... please let me know.

Looking for HowTos... i found this thread...[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

But the laptop seems to recognize the soundcard and drivers... and alsamixer was all maxed out.

We tinkered with this for a while to no result... so we gave up and went to sleep.
Next day I check her computer and sound runs perfectly. So I test it for hours, playing music, games, web radio.. etc.... not a flaw.. I restarted a couple of times and it worked pretty reliably. So... happy and all.. we thought it was the end of this problem.

That was yesterday...

Today the computer is mute again. No idea why...I've been looking around and this case looks very similar to ours...[URL="http://ubuntuforums.org/showthread.php?t=526030"]
http://ubuntuforums.org/showthread.php?t=526030[/URL]
We even have the same sound card it seems this is a result of aplay -l :

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

I am now wondering if this device needs a special driver for it.....
Any advice will be very very welcome.

---

### Post by ninhobomba on 2007-08-21
Well... once again, it's me and I have news... or something...

Going over the Comprehensive Sound Guide I already linked to on this same thread, (and which by the way I also found here (but wikified) : 
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
... I decided we should try the "getting the ALSA drivers from a *fresh* kernel" thing.

Turns out it worked.... the laptop is now playing sound correctly. At least for now... I just hope it stays this way.

Hope this info is useful for someone.
Ill report any new stuff on this,

---

