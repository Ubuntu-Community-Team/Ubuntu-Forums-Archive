---
title: "Problems with freezing and sound"
date: 2008-06-14
forum: Hardware
---

### Post by Herbonator on 2008-06-14
I am having some problems on my HP dv2000 with it freezing sometimes (I suspect its related to videos) and sound.

Freezes seem to be happening when I am opening any kind of video, online or on the desktop and they completely lock my computer up, I cant do anything and have to hard power off.

The problem im having with sound is that if I play an avi and then try and play a flash video from the net, I dont get sound online. I have tried using VLC and MoviePlayer and get the same results with both.

I am using 8.04 and its a fairly clean install, only a few apps installed.

EDIT:
I have now also noticed that my sound problem is vice-versa too. If I first play some audio from the net and then try and watch a local video - I get no audio.

---

### Post by Herbonator on 2008-06-15
Eh.. I have also noticed that volume control buttons on my laptop have stopped working. They were working perfectly before. Just the down button seems to have stopped. It still brings up the OSD for the volume control but it doesnt lower the volume. It stays at 100%.

Wow, this thing is really falling apart on me.

---

### Post by Odrodzona-Sarmacja on 2008-06-15
I have exactly the same issue.
There is lots of talk about what is causing it and how to fix it.
Nvidia-glx/nvidia-glx-new and xorg are the main suspects.
Removing any of them for alternatives doesn't help. It gets just worser.

How to watch movies?
Download movies. Disable networking. Dettach network cables from your network card. Reboot computer. Watch movies.

---

### Post by Odrodzona-Sarmacja on 2008-06-15
Sound issue should be solved with changing player's sound driver from osd to alsa in its settings.

---

### Post by Herbonator on 2008-06-16
> **Odrodzona-Sarmacja said:**
> Sound issue should be solved with changing player's sound driver from osd to alsa in its settings.

Thanks but unfortunately it didnt work. If anyone else has any suggestions please let me know!

---

### Post by Herbonator on 2008-06-16
> **Odrodzona-Sarmacja said:**
> I have exactly the same issue.
There is lots of talk about what is causing it and how to fix it.
Nvidia-glx/nvidia-glx-new and xorg are the main suspects.
Removing any of them for alternatives doesn't help. It gets just worser.

How to watch movies?
Download movies. Disable networking. Dettach network cables from your network card. Reboot computer. Watch movies.

I dont actually have an Nvidia graphics card though? I'm not sure what xorg is so I cant comment on that.

---

### Post by Herbonator on 2008-06-16
Hmm I have just noticed that VLC is still silent but MoviePlayer is now working. I may have a decent workaround. Let me test it for a few days before I confirm that.

Still my volume buttons have stopped working and I have not been able to resolve that. Any sugguestions? I havent had a freeze for a couple days either.

---

### Post by Odrodzona-Sarmacja on 2008-06-16
> **Herbonator said:**
> Still my volume buttons have stopped working and I have not been able to resolve that. Any sugguestions? I havent had a freeze for a couple days either.

You can install a mixergui.
Maybe you can enable some sound options there (or disable some unwanted).

---

### Post by Nepherte on 2008-06-16
Not being able to listen to sound in 2 applications at once is most likely related to pulseaudio. There is a whole how to with fixes: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Odrodzona-Sarmacja on 2008-06-16
I was getting some issues with sound's playback only when i was having an app on my desktop configured with other driver instead of alsa.

---

### Post by TracyO on 2008-07-03
I'm having similar trouble.  I notice it on YouTube, and I think occasionally on Rhythmbox where the sound will not go down.  I can't get it down using the buttons on my Dell Inspiron 1525 or through the icon the system tray.  Sometimes even muting it will just make it go to the highest point.

I'm using Gutsy.

The sound mechanisms freeze, and then a little while later, they are okay.

Tracy

---

