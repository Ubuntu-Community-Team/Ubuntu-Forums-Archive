---
title: "Scratchy sound on ALC 888 but not if keep the mouse moving!"
date: 2008-10-03
forum: Hardware
---

### Post by tydfil on 2008-10-03
Hardy AMD64

Just upgraded to XFX 8200 mb.  AlC 888 is scratchy as if lots of other processes interfere with the sound. Have read on other forums that I needed to update alsa and followed several guides to improve sound with not change at all.  Then I noticed sound was perfect as long as I keep my mouse on the move.  I think this sound like IRQ rather tha OS.  Have tied PS2 Mouse and USB mouse, both give same effect.  Don't have a serial mouse to try.  It seems unlikely that MB is the problem as they should work together.

Any ideas

---

### Post by tydfil on 2008-10-03
Update on my problem.

Get a few programs running and keep em busy and sound is great?  Get a few downloads going sound is fine?  It appears to be bad when there is nothing else going on?

---

### Post by TheLions on 2008-10-03
are you using pulseaudio or ALSA???

if you are using PulseAudio check here how to fix it:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

check part d

---

### Post by markbuntu on 2008-10-03
Some nvidia sound chips have that problem, it is fixed in the 2.6.27 kernel which is in Intrepid so you might just wait a few weeks.

---

### Post by tydfil on 2008-10-04
Thanks TheLions for the info, but I am not using Pulse Audio.  Should I be? Only ALSA installed.  Thanks Markbuntu maybe I will wait as you suggest.  Is Pulse Audio a better choice?

:D

---

### Post by TheLions on 2008-10-04
PulseAudio is add-on on ALSA, but probably it wont solve your problems.
Yes it is better cause it solves the problem with multiple applications trying to play sound simultaneously.

---

### Post by tydfil on 2008-10-05
Thanks again TheLions.  I have now installed PulseAudio, but as you point out it hasn't solved the problem.  Will use an old SB 5.1 for now, if I can get that to work.

---

