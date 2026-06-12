---
title: "No sound card view or useable?"
date: 2010-02-18
forum: Hardware
---

### Post by Turk4n on 2010-02-18
I have recently installed ubuntu again after a reformat, now using 9.10(again), and having a sound card problem, I can't seem to select my soundcard in sound preferences and it
This is all I seem to be able to see, and I really want my sound card to just work...Help me please !

[ATTACH]147442[/ATTACH]

---

### Post by ajgreeny on 2010-02-18
It looks to be already selected.

If you are getting no sound use the terminal and enter ```
alsamixer
```to get a terminal sound mixer system.  Use cursor keys to go sideways and to raise and lower levels, "M" to mute and unmute, and tab to move from playback to capture to all.  Use esc to exit and save settings.

You may find several sliders in that which are either set too low, or even muted.

---

### Post by Turk4n on 2010-02-18
> **ajgreeny said:**
> It looks to be already selected.

If you are getting no sound use the terminal and enter ```
alsamixer
```to get a terminal sound mixer system.  Use cursor keys to go sideways and to raise and lower levels, "M" to mute and unmute, and tab to move from playback to capture to all.  Use esc to exit and save settings.

You may find several sliders in that which are either set too low, or even muted.

No, I don't want to use my HDMI when I have my 3.5mm jacket in and wishing to listen for music........

---

