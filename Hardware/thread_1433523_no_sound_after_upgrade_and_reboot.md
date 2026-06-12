---
title: "no sound after upgrade and reboot"
date: 2010-03-19
forum: Hardware
---

### Post by snitko on 2010-03-19
Update manager updated a few libs recently (can't remember which ones, but it was definitely not linux headers). Then, after reboot the sound stopped working. The song in rhythmbox would go on playing visually and there is no indication in Sound Preferences that the hardware is not working properly. Yet no sound is coming out of speakers. I tested the sound card in windows - it worked, so it's definitely not the hardware problem.

I have Creative Sound Blaster Audigy 1 card and Ubuntu 9.10 x64. Any ideas?

---

### Post by sam.reader on 2010-03-19
I think you will need to install the drivers of you card again.
Since the updates must have been also included with some sound drivers for the OS this problem might have occurred.
Just uninstall your hardware drivers and reinstall them again.
Let us know if this has solved your problem or not.

---

### Post by snitko on 2010-03-19
The problem is - I don't know which drivers to (re)install. When I first installed Ubuntu, the sound card worked out of the box. Where should I look for them? Creative does not have official Linux drivers for this card.

---

### Post by snitko on 2010-03-19
Okay, I reinstalled alsa, and installed alsa-tools. It seems to work now, but it was a bit voodoo magic. Didn't get it.

---

