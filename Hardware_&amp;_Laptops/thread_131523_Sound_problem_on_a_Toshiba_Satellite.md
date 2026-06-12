---
title: "Sound problem on a Toshiba Satellite"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by sean_naes on 2006-02-16
So I've been having odd freezes for a while, where I could continue to use the mouse, switch workspaces, and use open programs, but couldn't use any of the menu panels, and gnome becomes pretty much useless.  Ctrl-alt-backspace sort of works, but doesn't actually finish restarting the desktop, and I can't log back in.
I now believe it has something to do with sound.  It always happened while I was playing something in rhythmbox, but generally if I'm on my computer for a while I'm listening to something in rhythmbox, so I didn't think that's what was causing it (sound playback stops when the crash happens).  However, I've tried not using it for a couple days, and haven't had a crash.  Today I installed XMMS, and still haven't had the same type of crash, but I have had problems - XMMS will just close, or stop responding and I need to force quit it.  I would also have strange skips, where the sound would go a bit fuzzy and then it'd start playing the next song.
The XMMS crashes at least didn't bring the whole system down with them, but still, this leads me to believe that some kind of sound problem is at the bottom of this.
I checked my .xsession-errors file, and found this line:
ALSA lib pcm_dmix.c:802: (snd_pcm_dmix_open) unable to open slave
many many times, so there must be something or other going on with my sound.  I'm not sure where else to look to find out what's going wrong.
The files are all AAC/MP4 (all ripped in iTunes on Windows).

Oh, after these crashes, if I try to run aplay on a wav file in the terminal (ctrl-alt-f1 works) it gives me this error:
aplay: xrun:1062: read/write error, state = PREPARED

Any ideas?

Edit: oh yeah, the laptop is a Toshiba Satellite A70-SC1, P4 3.33GHz with HT, I'm running the 686 kernel (though I have the same problems with the 386 and 686smp)

---

### Post by sean_naes on 2006-02-20
no ideas?

---

