---
title: "XPS 15 with Ubuntu 16.04 and SOUND."
date: 2016-05-05
forum: Hardware
---

### Post by baillou2 on 2016-05-05
So there's a fairly well documented problem with this laptop and sound issues. Specifically plugging in headphones kills all audio (headphones or otherwise) and only a reboot seems to bring it back.

BUT I've found that if I reboot the computer with the headphones already plugged in I can switch back and forth between external speakers and headphones in "sound settings". I just have to keep the 
headphones plugged in. If I take them out and plug them back in everything goes quiet again. As far as I can tell everything seems to be working fine when I check, but there simply is NO sound at all that actually
comes through. The various GUI applications I use say that the sound is outputting, but there's nothing until I reboot.

It's almost as if it's a hardware problem, and I would have thought so except both external and headphones do work, just so long as I don't unplug the headphones.

Can anyone explain what's going on here?

Thanks.

---

### Post by poltiser2 on 2016-05-05
Check alsa driver settings - it looks like the old story...

---

### Post by baillou2 on 2016-05-06
> **poltiser2 said:**
> Check alsa driver settings - it looks like the old story...


And how would I do that exactly? I've used Gnome Alsa Mixer to look a little more closely, but everything looks fine, except that there's no sound of course.

---

### Post by shinyblue on 2016-05-09
I have this problem too with 16.04 on Dell XPS 15 9550.

All was working fine, then one day it goes silent when plugging in my speakers to the headphone socket.

Looking at pavucontrol and/or "Sound settings" under Gnome it shows that the sound should be playing on the Headphones output port - the VU meter is bouncing up and down ok, but it's silent. Pull out the wire (or select internal speakers) and the sound switches to the internal speakers OK.

Last time this happened I fiddled for ages and then got distorted sound (sounds like some sort of cross-channel thing) and this only went a away with a complete re-install (which I did to try to fix a separate bug).

I ran **alsa-info.sh** from the command line and uploaded the info. Here's the URL it gave me to share:
[http://www.alsa-project.org/db/?f=06aa76739ef095fa20799210f33f7ebb379442a7]("http://www.alsa-project.org/db/?f=06aa76739ef095fa20799210f33f7ebb379442a7")

It's now happened again, having spent all Friday enjoying music, Monday morning turn on and silence! I've not done any upgrades since.

---

### Post by baillou2 on 2016-05-11
So here's my alsa-info.sh output [http://www.alsa-project.org/db/?f=d64b1a6af358012baa0273a64938ce4faa6396d0](http://www.alsa-project.org/db/?f=d64b1a6af358012baa0273a64938ce4faa6396d0)

I wish I knew what to do about this. It seems to be a pretty nasty bug. My hope is that this is a priority. But I have no idea how bugs are prioritized.

---

### Post by Torsten_Verolan on 2016-06-21
I'm having this same issue, though at the moment even reboots are not bringing sound back and the system is not detecting any soundcards at all.

---

### Post by dorian8 on 2016-06-22
There is currently (after some cold reboots) still no soundoutput through the build-in speakers. 
[http://www.alsa-project.org/db/?f=6a139b480fe8cc9b7809a98df808ddd047734b66](http://www.alsa-project.org/db/?f=6a139b480fe8cc9b7809a98df808ddd047734b66)

---

### Post by cmrk on 2016-07-01
+1 same problem, reboots no longer work...

---

