---
title: "Sound Blaster Z came... and went. [Ubuntu 16.04]"
date: 2017-12-01
forum: Hardware
---

### Post by ct77 on 2017-12-01
I have a PC with an onboard sound card, but also a *Sound Blaster Z* card installed.

  I use *Ubuntu 16.04*.

  For a long time, the *Sound Blaster Z* card hasn't worked in *Ubuntu* (it works in *Windows*, so the card isn't faulty).

  Here the other day, my sound suddenly wasn't working at all. I saw that my onboard sound card wasn't appearing on the list of output choices (under &#8220;System settings&#8221; -> &#8220;Sound&#8221;). Only the *Sound Blaster Z* card appeared (as it has before). I moved my S/PDIF cable from the onboard sound card to the *Sound Blaster Z* card and &#8211; halleluja! &#8211; there was sound!

  Weirdly, some days later things have changed again.

  I suddenly have no sound from the *Sound Blaster* card, and have to specifically turn the onboard sound card on (&#8220;Enabled&#8221;, not &#8220;Auto&#8221;) in the BIOS settings for it to show up in the list of choices in &#8220;Output&#8221; (&#8220;System settings&#8221; -> &#8220;Sound&#8221;). Then, moving the S/PDIF cable back to the onboard sound card, I can get sound again. (Weirdly, I can't get the list of input choices to show the mic input of the onboard sound card &#8211; only the *Sound Blaster* ones are showing. It wasn't like this before this whole series of changes began.)

  Weird. This was a sad process. I thought this finally would be the time when the *Sound Blaster Z* would work, and keep on doing so into the future. But I'm back to basic again.

  Anyone experienced this? Are there hopes in getting the *Sound Blaster Z* card to work again?

---

### Post by fredd2 on 2018-01-17
This card is troublesome. You can get it to work.

For example I have a headset with an audio and microphone jack. I need to plug in the microphone port in the back of the sound card, and it will work.

I have to make sure my case audio header is connected to the sound card, and then I can get audio working via the headphone port on the case, after enabling headphone automatic detection in alsamixer. Usually I have to replug the cable when I boot the cable, for it to detect it again. Sometimes it does not work and I have to try a new system boot and replug to see if it then works.

Sometimes if the system has been running for a few minutes and I do not have audio, replugging will not do anything. It is after a fresh boot the replugging trick works usually.

---

