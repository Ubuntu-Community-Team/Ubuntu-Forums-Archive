---
title: "sound not working in intrepid or vista"
date: 2008-12-23
forum: Hardware
---

### Post by LordIshamael on 2008-12-23
hey my sound suddenly stopped working yesterday evening/today morning sometime
it was working fine yesterday evening around 7:30 Indian Standard Time, but then this morning it was suddenly gone, so something must have happened in between
i dont think its an os issue because, as i said, it doesnt work in kubuntu intrepid or vista ultimate
intrepid shows in system settings>sound that an hda intel alc268 analog is present, but grayed out
but i think thats just something else and not the real card, i think there used to be two of those entries when my sound worked, now theres only one
aplay -l doesnt list any cards, as root it says no protocol specified, E:client-conf-x11.c: XOpenDisplay() failed

in vista it says no audio output device installed, under device manager there is no listing for any audio dewvice category, as if there is no device detected, let alone installed

even plugging in headphones (that i know work) is no good, no sound on either os

any idea how this happened and how to fix it?please?its really urgent that sound get working

---

### Post by Zorael on 2008-12-23
If it doesn't work in either OS, that suggests hardware failure, I'm afraid. Electronics fail too.

To be completely sure, you could try booting a live CD to make sure it isn't some setting. If you get sound there, that's weird. If you don't, you have a busted soundcard.

---

### Post by LordIshamael on 2008-12-23
i tried it from a live cd, it didnt work
i was inclined to agree with you - soundcard gone
just in case, i took it to a comp guy who i was visiting anyway for something else
he started it up in vista, and sound worked!
i rebooted into ubuntu, and sound was working there too
i took it home happily, booted up - no sound.

turns out he had booted up vista pressing ctrl-esc while it started, this made it work
so i booted into vista with ctrl-esc, did some work there, rebooted, am typing this from ubuntu with proper sound

still havent figured out why the sound stopped, if the problem will come back the way it did when i came home, or how to resolve the issue from ubuntu instead of the vista ctrl-esc option, but one thing is for sure - sounds working!

---

