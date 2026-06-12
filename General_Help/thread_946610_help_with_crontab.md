---
title: "help with crontab"
date: 2008-10-13
forum: General Help
---

### Post by sdlyr8 on 2008-10-13
I am trying to set up an alarm clock for my computer running by crontab, that every morning it runs a simple bash script that locks the computer and requires a password, turns up the master volume to full blast, and plays a certain loud annoying sound clip. I wrote the bash script and it works by running it myself. But when I set up the cronjob, the only step it does is turning up the volume. It doesn't lock the screen or change the song. Here's my bash script....
```
#!/bin/bash

amixer set Master 100%
gnome-screensaver-command -l
rhythmbox /full/path/to/song.mp3

```

And here's the out put from the cronjob...

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
cannot open display: 
Run 'rhythmbox --help' to see a full list of available command line options.

```

Does anyone know how I can fix this? I'm guessing I have to include which display but I don't know how... Thanks in advance!

---

### Post by sdlyr8 on 2008-10-19
bump

---

### Post by geirha on 2008-10-19
Set the DISPLAY variable for the script to :0.0 so gnome-screensaver-command and rhythmbox knows which display to run on. :0.0 is typically the first display, it will work as long as your user is logged in first (on Ctrl+Alt+F7)

```
* * * * * DISPLAY=:0.0 /path/to/script.bash
```

---

### Post by Sam on 2008-10-19
Because it's run "outside Gnome" so you cannot run a GUI application in "terminal mode". You need to specify the display to use when launching the command.

Find out your display number in Gnome with:
```
echo $DISPLAY
```

It should be something like ":0.0".

Then update your script:
```
# (previous lines go here)
rhythmbox --display=:0.0 /full/path/to/song.mp3
```

---

