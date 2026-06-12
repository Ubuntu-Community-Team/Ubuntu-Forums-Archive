---
title: "No Sound After Signing In"
date: 2010-05-09
forum: Hardware
---

### Post by treeclimber on 2010-05-09
I recently upgraded to Lucid on my Dell 1505n laptop.  I have an integrated soundcard on the Intel motherboard.  I can hear the bongos when my login page comes up, but no sound at all when I finally get on.  The computer recognizes the soundcard, it is turned on, but no sound.  I have tried changing the settings for the card, but it still isn't working.  I have never had a problem with it before.  I'm sure it is working or I wouldn't be able to hear the sounds at the beginning.  It is probably an easy fix, but I'm just not finding it.  Can anybody help?

---

### Post by khelben1979 on 2010-05-09
Have you tried the settings in [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")gui?

```
sudo apt-get install alsamixergui
```
will install it.

---

### Post by DarkN00b on 2010-05-09
You could also open a terminal window and type alsamixer. Make sure the "PC Speaker" setting is at max. That should fix your problem. This fixed the problem with my wife's Compaq.

Press the <ESC> key to exit alsamixer.

---

### Post by treeclimber on 2010-05-09
I installed alsamixerdui, as you suggested.  When I opened it, it didn't look like it was supposed to look (no colors, all gray).  I nevertheless, saw it had my soundcard listed.  It showed master and capture at the bottom. I clicked on them and the locks, which closed.  I went under preferences, clicked on sounds, then changed setting to duplex analog stereo.  Then the sounds worked!  But I still can't hear sound on any videos on the Internet. I can hear it fine on any videos on my computer.  I figure it is some silly setting I'm not finding.  Anymore ideas?

---

### Post by khelben1979 on 2010-05-09
> **treeclimber said:**
> I installed alsamixerdui, as you suggested.  When I opened it, it didn't look like it was supposed to look (no colors, all gray).
It's just as it should look like, all gray, yes.

> **treeclimber said:**
> 
I nevertheless, saw it had my soundcard listed.  It showed master and capture at the bottom. I clicked on them and the locks, which closed.  I went under preferences, clicked on sounds, then changed setting to duplex analog stereo.  Then the sounds worked!
Progress is good!  

> **treeclimber said:**
> 
But I still can't hear sound on any videos on the Internet. I can hear it fine on any videos on my computer.  I figure it is some silly setting I'm not finding.  Anymore ideas?
You say you can't hear anything from videos on internet. Is it YouTube or anything else on the web which uses [Adobe flash]("http://en.wikipedia.org/wiki/Adobe_flash")?

---

### Post by treeclimber on 2010-05-09
yep, it was the Flashplayer plugin.  I uninstalled it, and reinstalled it now everything is working!  And I did that before I got back on here!  Pat myself on the back!  And Thank You!

---

