---
title: "Gnome Radio No Sound When Tuned"
date: 2008-11-08
forum: General Help
---

### Post by Super TWiT on 2008-11-08
Hi, I am having a problem where gnome radio won't output any sound.  However, this is only when it is stopped on a station.  When it is scanning, I can here the audio of those stations clearly.  It will even find local stations too.  But when it stops on one of those stations, there is no sound.  The second I exit gnome radio, I can here the audio of the last station it said it tuned to. Gradio works, but it doesen't incorporate any volume control as I get my output through the line in on my computer.  The output is set in gnome radio to be line in, but still nothing.  Can anyone help me?  I have already tried running it like this,```
gnomeradio --mixer=/dev/mixer:pcm
``` but still I get nothing.  I also can't seem to get fm (the app from fmtools) to work with it either.

---

### Post by Super TWiT on 2008-11-09
I figured out a few things since last night, apparently I can only get sound from gnome radio after it exits if mute on exit IS checked.  Also, I get sound when fm mutes radio and no sound when it turns on radio.  Weird.

---

