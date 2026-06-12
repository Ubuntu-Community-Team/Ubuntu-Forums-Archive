---
title: "Mic not working on hp dv6560el"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by barone_birra on 2008-01-30
Hello!

I've installed Ubuntu Gutsy Gibbon on my HP DV6560EL.
I succeded in installing all exept the microphone.
If I go on System>Preference>Audio and test Audio Acquisition get this error:

Fallita costruzione pipeline di prova per «gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat»

I have used ALSA Mixer and checked all boxes to use Alsa and made sure everything is unmuted.

I'm very sad. I removed Vista that's terrible, but I can't use Skype for Videocall...

:confused:

---

### Post by cdtech on 2008-01-30
There are several other threads with this same issue on the HP.

Use your alsamixer

Press f5 to bring up all controls and select IntMic or the LineIn  **using the arrow keys**. Press the **space** key to select the IntMic or the LineIn (which ever works for ya) as the capture.

Should be good to go.....

This is my alsamixer when I press f5..

[ATTACH]58084[/ATTACH]

---

### Post by barone_birra on 2008-01-31
I read other posts and tried this procedure but it doesn't work..

I tried also an external mic connected to the mic jack, but nothing...

---

