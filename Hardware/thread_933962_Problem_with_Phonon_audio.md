---
title: "Problem with Phonon audio"
date: 2008-09-30
forum: Hardware
---

### Post by cewan on 2008-09-30
Hello!
I get this whenever i start my music player. What can I do to make it disappear? 

```
Phonon
The audio playback device HDA Nvidia (AD198x analog) does not work. falling back to HDA Nvidia (AD198x analog).
```

I am running Kubuntu 8.04.1 with KDE 4.1.1.

The sound is working, but song switching is kinda weird.

BR

---

### Post by victorgreen on 2009-04-26
Just upgraded to Jaunty 64 on straight Ubuntu and got Amarok 2 for first time... and it wont play anything AND removed the gui options to edit desired default playback device. It is totally unusable now.

---

### Post by Tuxi on 2009-05-02
I stumbled upon a solution that worked for me.  Install phonon-backend-xine and select that as your preferred plugin in System Settings/Multimedia.

---

### Post by steevc on 2009-06-05
I get a similar error message except that it is falling back to the digital output and I lose sound. I already have the Xine backend. I installed 9.04  on this PC a while back and get this problem now and again.

Any other ideas?

---

### Post by steevc on 2009-07-29
Still getting this problem. Sound can be fine for a while then may suddenly stop with the above message from Amarok. I was streaming audio from last.fm today when it suddenly happened. The only way I know how to get sound back is to restart the PC.

The problem also occurs sometimes when a second person logs in and ends up with no sound. We each have our own accounts and often have several people logged in and switch between the sessions.

Most references to such problems mention using the Phonon Xine backend, which I already do, and removing Pulseaudio, which I don't have installed.

---

### Post by gunksta on 2009-07-31
You can also try dropping to a console (konsole) and playing with alsamixer. For some odd reason I had two computers with Kubuntu installed and had the PCM set to mute. . . . which negates the audio experience.

---

