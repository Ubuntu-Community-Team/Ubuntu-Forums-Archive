---
title: "How did I kill my audio?"
date: 2008-12-16
forum: Hardware
---

### Post by Twizzle on 2008-12-16
I had Mythbuntu installed on a system based around an Abit AV8 motherboard. I was using my Creative Audigy sound card and had the whole thing linked to my TV.

A couple of days ago I turned it on but there was no sound. I tried all the settings but to no avail. I then removed the sound card and enabled the on board sound in the bios. Rebooted but again no sound. I then reinstalled thinking that there was some sort of driver conflict or I had updated something I should not have done... Nothing.

I even tried windows but again no sound.

I have no understanding of how motherboards work but is there some chip that could have blown that made my sound go? Everything else seems to work. The on board chip detects which plug the speakers are plugged into and there are no errors.

:confused:

---

### Post by nixscripter on 2008-12-16
First thing's first: I would suggest checking your sound levels.

Open a command line window and run: ```
alsamixer
``` to make sure the levels are all up. This will also check and make sure ALSA is running, which is necessary to drive the sound card.

---

### Post by Twizzle on 2008-12-18
Thank you for the suggestion and an apology for the delay.

Ok, I tried the live cd of Mythbuntu which started fine. Ran Alsamixer which also started fine and shows volume on all for playback.

I have now tried an avi(xvid) and mpg file but neither has any audio. I know the speakers work and I also get that buzzing noise every time I plug them in  / take them out of the sockets on the motherboard.

I am really confused by this. How can both a sound card and the on board sound chip die at the same time!

---

### Post by donkyhotay on 2008-12-18
Sounds more like a software/configuration issue to me. In my experience unless something is SERIOUSLY wrong with your hardware losing all audio is either something with the ALSA volume controls or with ALSA itself. I'm not saying it isn't your hardware, just that it's less likely and I would take a look at ALSA first. You mentioned trying to play a avi/mpg file, are you capapble of getting sound from anything at all? Try downloading a small program that plays sound (burgerspace would probably work) to make certain this isn't some wierd codec issue.

---

