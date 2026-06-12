---
title: "Video Files Won't play"
date: 2008-07-10
forum: Hardware
---

### Post by Daug on 2008-07-10
Hello All--

I've got multimedia playback problems on my Toshiba Satellite M20 with Hardy installed.  The laptop has motherboard (Intel) VRAM (32MB).  I've also got many different codecs and players installed from many different sources, including from [this how-to]("http://ubuntutip.googlepages.com/multimediaubuntustep1").

The problem: when I try to play any multimedia filetype (avi,mpeg,mp4,wmv,mov,qt), I get a blank screen with no sound and no cursor (backlight is still on).  I am unable to recover from this screen, with any key-combo (ctrl-alt-f1, etc.).  I'm guessing the default video driver (which works fine for all other OS functions) is pooping out.  I this is the X11 driver?  I'm not sure; and I guess that's what my question is: how do I install/change the default video driver so that multimedia playback will work?

PS: Ultimately I'd like to have one player (hopefully VLC) to work for everything, but first I'd like to get any playback working at all...

Many thanks in advance, and Ubuntu ROCKS!!

-Daug

---

### Post by ljonesj on 2008-07-10
it may be that u dont have enough vram can u increase the amount vram in the bios and how much regular ram and what processor do u have

---

### Post by Daug on 2008-07-10
Thanks for the response, jones--

Processor is 1.3Mhz Pentium M

RAM is 768MB

I didn't think about the fact that it may not have enough vram.  But these files are test files; small videos that even my palm can play...

---

### Post by Daug on 2008-07-11
Interesting development:

I've discovered that I can play all of the formats I mentioned earlier through Firefox.  I can also get fullscreen playback as well, although there is no visible controller except for when I play mp4 files.  I can control play/pause, scanning and volume, though, using spacebar, and ctrl/alt arrows, though.  I'm not sure, but it feels like Firefox is using VLC to render the videos, just from the controls and icons...

Once I used Firefox to open all of the filetypes, Ubuntu assigned it as the default app for them.  A couple of times, I got the blank screen again when I simply tried to double-click the files.  I think it helps to have FF loaded first, then open the files.

For the foreseeable future, I'm happy to use FF to play movies, as it has all of the functionality of any other player.  However, I am still curious why the standalone players themselves don't work, if anyone has any ideas.

Thanks

---

