---
title: "Sudden sounds issue after external drive accidentally removed..."
date: 2009-03-15
forum: Hardware
---

### Post by raintheory on 2009-03-15
Sort of a strange end-result, but my sound suddenly isn't working on my ThinkPad T61 Intrepid install.  It has worked fine for at least 2- months prior to this...

Whilst watching a video, the external drive the video was on was accidentally unplugged.  First I tried just plugging it back in, but no messages or anything, and no drive.  After a reboot I got the familiar warning about unsafe removal, etc...  I then proceeded to plug the drive into a windows box and scan for/fix errors.

Anyway, now trying to play any mp3 files (on local drive) produces nothing but silence.  If anyone has any advice or steps I could take to diagnose the issue, please share..

Also, the hard drive still gets an error and pretty much tells me I have to force mount in order to use it...  but that is another issue.

Thanks,

-Aaron

---

### Post by MyR on 2009-03-15
well there's a ton of stuff you could try.  test the hardware with a live cd... make sure sound isn't muted... make sure volume is up... try some different music players/apps (vlc, amarok, totem-xine, etc) try some different audio formats (ogg, wav, etc)... right click the volume icon on panel and play around with volume control.. test sound output or change the device in system > preferences > sound...  reload alsa from command line: alsa reload  ... try killing pulseaudio from system monitor... *completely* remove pulseaudio & alsa & then reinstall.

good luck!

peace

---

### Post by raintheory on 2009-03-15
thanks for the response.  here is what i have done so far;

  - fiddled around with the volume control (to make sure nothing was muted that shouldn't be.)

  - switched between ALSA and OSS.

  - ~$ sudo apt-get **remove** pulseaudio (this also removed ubuntu-dektop and ubuntustudio-desktop along with pulseaudio).  ~$ sudo apt-get **install** pulseaudio ubuntu-desktop ubuntustudio-desktop

  - ~$ sudo apt-get **remove** alsa (which removed alsa-base).  ~$ sudo apt-get **install** alsa

  - tried various formats in various players (VLC, Rhythmbox, Movie Player, Audacity).

  - killed pulseaudio from system monitor.

  - tried 3 previous kernels on boot. 

  ...all to no avail.  I'll need to grab the liveCD from my parents' house today before I can go that route.  

   thanks so much for the replies, hopefully I can get this squared away without having to do a complete reinstall of ubuntu.  I've spent an inordinate amount of time setting everything up the way I like it and it would take longer than I care to spend to do that all over again.  

  -aA

---

### Post by raintheory on 2009-03-16
The liveCD resluted in sound, so it must've been something software/OS related.  I went ahead and reinstalled today after moving everything I needed to an external drive.

thanks for the help!

-aA

---

### Post by raintheory on 2009-03-16
Well after a fresh install and setup, I am experiencing the same issue once more...   This time there was no external drive accidentally unplugged prior to the issue.  Therefore I am hesitant to assume that caused the initial issue.

I've tried various formats in various players, as well as all of the aforementioned troubleshooting.  It worked fine all day today until this evening.

I'd really like to get this working.  I'm using Ubuntu 8.10.  Any help or direction is **greatly** appreciated.  Thanks in advance!

-Aaron

---

### Post by MyR on 2009-03-16
if you have a wav file handy, in a terminal try:
aplay /path/to/wav
to see if you get any useful error messages from the terminal.
or run some media players from the terminal and see if they spit out anything interesting.
try plugging in or unplugging headphones or external speakers.

peace

---

### Post by raintheory on 2009-03-16
While in my 'Music' directory, ~/Music$ aplay filename.wav results in *"Can't open input file 'filename.wav': No such file or directory"* even though **ls** shows the file in the directory.

Running vlc via terminal and then the file showed nothing of interest in terminal, no errors or any relevant info...

Thanks,

-aA

EDIT: Tried external speakers and they actually work(?), but the internal speaker that used to work on my laptop does not.  ...Interesting.  I use external speakers most of the time so this isn't as big of an issue as I had originally thought, but still would be nice to figure out...

---

### Post by raintheory on 2009-03-17
Okay so here's what I've got so far...  Sound works, *but*.

Previously when I would unplug the external speakers, the sound would switch over to the internal speaker  automatically.  This no longer seems to be the case.  

In order to get the internal speaker to work, I have to go under the *switches* tab in Volume Control (somehow I didn't see this before) and select *"Speaker"*.  Then, in order to play via the external speakers I have to go into the same place and select *"Headphone"*.  

This never used to be the case, is there a config file somewhere I can take a look at?  ...Would save me a few steps when switching from internal to external speakers.  

:)

Thanks so much again for your replies.

---

### Post by MyR on 2009-03-17
Try this:
Right-click on the volume control icon in the panel and click on Open Volume Control. 
From the menu choose Edit->Preferences. 
Tick the checkbox Headphone Jack Sense and close the menu. 
Go to the Switches tab and enable Headphone Jack Sense.

If that doesn't work, I'd recommend reporting a bug on launchpad.  Or you could report the bug either way to benefit others.

Happy St. Patrick's Day!

---

### Post by raintheory on 2009-03-17
Hmm, I actually see no toolbar at all (for edit/prefs) when I open volume control...  

:confused:

---

### Post by MyR on 2009-03-17
> **raintheory said:**
> Hmm, I actually see no toolbar at all (for edit/prefs) when I open volume control...

Sorry it's under the switches tab
If it's not there, open prefernces in the volume control and enable it.

peace

---

