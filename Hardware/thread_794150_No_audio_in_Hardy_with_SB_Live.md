---
title: "No audio in Hardy with SB Live"
date: 2008-05-14
forum: Hardware
---

### Post by SFauconnier on 2008-05-14
I have been messing with my Audio settings for hours now, been googleing like crazy, but without any luck.

I have the following audio hardware (as shown with lspci):
01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)

I have 2 stereo speakers connected to it.

I tried multiple settings with System>Preferences>Sound and been messing with AlsaMixer and [paconfig]("http://ubuntuforums.org/showthread.php?t=759147").

When I use paconfig, I have sound after a reboot (albeit distorted), but my resolution/video settings get all messed up (:confused:). Upon a second reboot, my resolution/video settings are back to normal(:confused:) and I hear a sounds at the login screen (twice! :confused:), but once logged in, the sound is gone again.
If I try to play a music file or try to test the sound in System>Preferences>Sound, my speakers start creating very rapid, distorted sound pulses (dont know how to describe it otherwise). The pulses dont go away, even if I close everything.

Anyone who can help me out?

---

### Post by SFauconnier on 2008-05-14
Alright, I reinstalled Ubuntu with my onboard sound disabled in BIOS.
I got a sound at the login screen (twice again) and this time I also get some sound output when messing with the sound preferences. However, none of the available settings work.

I found out, however, that the "pulses" I was talking about aren't really pulses, but just sounds I tried to play in a very very very very slow motion. Like 10 seconds = 5mins of sound.

---

