---
title: "Ubuntu 8.10 - No sound"
date: 2008-12-13
forum: Hardware
---

### Post by francesthemutes on 2008-12-13
I'm using a Compaq Presario R3000 and I have no sound.

I had sound during the Live CD, and after installing all updates, I had sound for a while but when I went to view a YouTube video it was too loud and I used the buttons on the side of the laptop to turn down the sound. After pressing the button, the sound was gone. I've restarted the laptop but still have no sound. I've also tried many of the different options in the Sound Preferences but still to no avail.

Anything I can do?

---

### Post by El Rogueo on 2008-12-14
> **francesthemutes said:**
> I used the buttons on the side of the laptop to turn down the sound. After pressing the button, the sound was gone.

Did your laptop have any sort of proprietary drivers to interact with the sound buttons it has? It's possible there was some sort of conflict between ubuntu saying "keep the sound loud" and you manually having the system respond with "oh no you don't".

Assuming you haven't accumulated a lot of personal files, you could probably just reinstall ubuntu cleanly and hope it got rid of the conflict. Alternatively, reinstalling the ALSA drivers might help.

A good way to test this theory before you do anything like reinstallation would be to put the LiveCD back in. If the sound works fine on the LiveCD, you know it's related to your use of laptop key actions that ubuntu might not support for your model, depending on how they're implemented. However, if you put the liveCD back in and the sound *still* doesn't work, that's an indication that you have a hardware problem with your sound device, independent of the operating system on the computer.

I think it's most likely that it's just an unlucky combination of Ubuntu saying one thing and you manually overriding it, but if you're lucky you can use synaptic to --purge your sound drivers, and then reinstall them and hope for the best.

---

### Post by Butterbelly on 2008-12-16
Useful advice.  Unfortunately my laptop (HP) worked fine-and-dandy prior to upgrading to 8.10 so I know I shouldn't have a hardware conflict, should I??  I tried removing Pulse (which I think is the 8.10 sound default) but synaptic gives me a rather worrying message that it will also remove the desktop, oo-er?!

But I'll try reloading ALSA as suggested and hope for the best, otherwise I guess I'll have to whistle my own accompaniment to stuff....

---

