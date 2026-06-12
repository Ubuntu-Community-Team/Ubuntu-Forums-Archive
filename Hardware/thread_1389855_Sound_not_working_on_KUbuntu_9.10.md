---
title: "Sound not working on K/Ubuntu 9.10"
date: 2010-01-24
forum: Hardware
---

### Post by chellrose on 2010-01-24
I have a Toshiba Satellite T135-S1309 running dual-boot Win7 and Ubuntu 9.10 (both GNOME & KDE installed, though I use KDE more frequently).  The sound does not work, although everything in Settings seems to indicate that it should be working.

lspci showed the following for audio, in case it's helpful:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```Any suggestions?

Thanks. =)

---

### Post by luffy_chan_19 on 2010-01-24
i would sugest goung to system->preferences->sound and click the output tab and turn up the volume of the device from there and test it to see that it is working. i have this problem all the time, except when i play anything all i hear is the speakes crackling. hope this helps

---

### Post by chellrose on 2010-01-25
> **luffy_chan_19 said:**
> i would sugest goung to system->preferences->sound and click the output tab and turn up the volume of the device from there and test it to see that it is working. i have this problem all the time, except when i play anything all i hear is the speakes crackling. hope this helps

edit: nvm.  Just found the "Mixer" option in KDE, and that seems to have fixed everything.  Thanks! =)

Thanks.  That apparently worked in GNOME, but when I switched back to KDE, there was again no sound (though I did hear a slight crackle when I messed with the volume slider).  Can you (or anyone) suggest a similar option for KDE (3)?

In K Menu -> System Settings -> Sound, clicking the "Test Sound" button resulted in some serious speaker crackle.  There doesn't seem to be an option to change the output volume, though.  The icon in the panel doesn't do anything.

---

### Post by luffy_chan_19 on 2010-01-25
> **Sissy13 said:**
> edit: nvm.  Just found the "Mixer" option in KDE, and that seems to have fixed everything.  Thanks! =)

Thanks.  That apparently worked in GNOME, but when I switched back to KDE, there was again no sound (though I did hear a slight crackle when I messed with the volume slider).  Can you (or anyone) suggest a similar option for KDE (3)?

In K Menu -> System Settings -> Sound, clicking the "Test Sound" button resulted in some serious speaker crackle.  There doesn't seem to be an option to change the output volume, though.  The icon in the panel doesn't do anything.


im not sure about KDE but it may just be a similar problem of the output volume being either muted or not turned up at all turning the slider up on the volume up at the right top corner does nothing to fix this, you have to go to the volume preferences to turn up the output volume. if you are running 9.10 when you go to the sound preferences there should be a tab called output, at the top of the window should be a output volume slider. the sound preferences window should look like the picture in the attachment 


[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by chellrose on 2010-01-27
Thanks; I got it working on KDE as well.  Just one lingering problem -- on login, the speakers crackle rather than playing the login sound.  I tried a sound test in settings; sometimes it worked, sometimes it just crackled, and sometimes it played a combination of sound/crackle.  I see that you've had trouble with crackle too.

However, the sound *appears* to work well the rest of the time, so I can live with the login crackle.
This is how I resolved the KDE 3 muted sound problem: right-click on the volume icon in the panel, and open Mixer.  Turn up the slider under KMix.

---

