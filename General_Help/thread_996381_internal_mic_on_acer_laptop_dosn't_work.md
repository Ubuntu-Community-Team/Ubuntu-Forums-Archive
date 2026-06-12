---
title: "internal mic on acer laptop dosn't work"
date: 2008-11-28
forum: General Help
---

### Post by verby on 2008-11-28
hi,
I have aspire 5520 and internal mic, doesn't work. I have checked with a cheap mic, so I know it is recording, but when I change to internal mic, nothing... any ideas?

---

### Post by jgoguen on 2008-11-28
Check that your internal mic is set to be used for recording.  Right-click on the sound applet (looks like a speaker) and choose "Open Volume Control".  Go to the "Switches" tab and make sure 'IntMic' is checked.  Then go to the "Recording" tab, make sure 'IntMic' volume is up.  There's two icons below it, one of a speaker and one of a mic.  Make sure they both have no red X over them.  Click the icon if so.  That should turn on your interal mic.

---

### Post by verby on 2008-11-29
the problem is I don't have switch tab, only playback/recording/options and I'm using hda nvidia (alsa mixer) should I change in sound to pulse?
btw: in options I have checked internal mic.

---

### Post by jgoguen on 2008-11-29
Try clicking on the Preferences button, make sure all the checkboxes in the window that appears are checked.  Then try again, hopefully that exposes the Switches tab.  If not, we'll try going through alsamixer.

What version of Ubuntu are you using?

---

### Post by verby on 2008-12-01
hi,
I've checked all the boxes and there is no switch available.
I'm using 8.10 (pulse) and on 8.04 it did work with alsa.
Is there a way to return everything to alsa?

---

### Post by jgoguen on 2008-12-01
I'm sure it's possible, I just don't know how off the top of my head.  Search the forums, or maybe someone browsing here will know.  Could you check alsamixer to make sure the internal mic is set to be the one used in there?  Open a terminal (Applications -> Accessories -> Terminal) and type this command:

```
alsamixer -D hw:0
```That will bring up the alsamixer interface.  You may want to maximize the Terminal window to make sure everything fits properly.  At the top left, you will see some information: Card, Chip, View, and Item.  Beside View, you should see at least three items: Playback, Capture, and All.  Press the Tab key until All is highlighted with brackets around it.  At the far right end, you should see a columns with "IntMic" under it and no volume indicator.  Press the right arrow key until this one is highlighted, and push the space bar so "CAPTUR" appears under it.  Then, for each other column with "IntMic", highlight it and push the up arrow key until the bar is full.  Once that's done, push Escape to exit and see if your internal mic works. I've attached a screenshot of my alsamixer interface to give you an idea of what you're looking for.  Yours may look slightly different depending on your hardware.  Note the "IntMic" columns on the right, and "All" is highlighted.

---

### Post by verby on 2008-12-01
see my attch. I did mark internal and vol on it. no success.
I've checked with my win partition, so I know it works.

---

### Post by jgoguen on 2008-12-01
I wonder if your 'Input So' should be marked with 'CAPTUR' instead.  Beyond that I'm not sure.  Hopefully someone else browsing can chime in and give some other ideas, or how to switch to ALSA.

---

### Post by tmarthal on 2009-04-16
It does work. I am using 9.04, but it is an alsamixer configuration issue, rather than a ubuntu version number. 

On a clean install, note that the OS does not set the capture device correctly. I am using an Acer Aspire 4530 laptop, but the internal microphone device (up near the webcam) is the same I believe. 

Run 'alsamixer' in the CLI, tab over to the [Capture] settings. Change the [Capture] setting 'Input Source' (not 'Input Source 1') to 'Front Mic'. Make sure that the capture input it set somewhere, and it should work. 


I searched for this topic, and this thread came up, even though it is 3 months old; hopefully this will help with getting your microphone and Skype and Sound Recorder working.

---

### Post by NewatUbunt on 2009-05-04
I just installed 9.04 Ubuntu on my Aspire One and also cannot get the internal microphone to work.  I brought up the "AlsaMixer" application in a terminal window and "Front Mi" is displayed for "<Input So>" in the "[Capture]" tab.  But neither Skype nor the sound recorder program will record any sound.

This is a fresh install (just did it today).  

Does anyone have any new help for this?  I've searched other threads/forums but nothing seems to work.

Thanks,
Bert

---

### Post by cabez0n on 2009-05-12
I have tried almost everything recommended on the bug reports but haven't had any luck with getting the internal mic to work. 

You might want to check out bug reports on this:
[https://bugs.launchpad.net/ubuntu/+bug/269294](https://bugs.launchpad.net/ubuntu/+bug/269294)

---

