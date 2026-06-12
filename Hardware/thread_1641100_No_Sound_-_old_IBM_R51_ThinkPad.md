---
title: "No Sound - old IBM R51 ThinkPad"
date: 2010-12-08
forum: Hardware
---

### Post by jhaensly on 2010-12-08
I recently installed XUbuntu onto an old ThinkPad that was lying around.  I managed to get everything working but the sound.  The sound worked in XP, so it's not a hardware issue.  One website ([http://www.linlap.com/wiki/ibm-lenovo+thinkpad+r51)recommended](http://www.linlap.com/wiki/ibm-lenovo+thinkpad+r51)recommended) the snd-intel8x0 module, but that seems to be running:

```
~$ lsmod
Module                  Size  Used by
snd_intel8x0           25588  7 
...
```

If it's helpful:
```
~$ uname -a
Linux eve 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```

If anyone has a suggestion, I'm at work and could really use some music :-P

---

### Post by boggie105 on 2010-12-22
Jhaensly,  I recently installed Ubuntu on my IBM R51 and the sound was working but now seems to have stopped working.  Did you find a fix for this?

Also - Have you had trouble with your forward slash key?  Mine does not work but Shift + forward slash does make the question mark.....  What keyboard layout are you using?

- Boggie

---

### Post by jhaensly on 2010-12-27
I did, but hell if I know how.  I must have tried half a dozen different fixes posted in the forums or old wiki pages without success, then, after a restart, the sound started working again.  The volume controls on the keyboard work but the software doesn't see them (so I can change the volume on the keyboard and the volume sliders on the sound control panel stay 100%), which is annoying but not annoying enough for me to keep messing with it.

I wish I had a better answer for you.  Good luck.

---

