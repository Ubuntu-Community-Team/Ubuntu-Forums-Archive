---
title: "Sound not working (MAudio Delta 1010)"
date: 2008-11-02
forum: General Help
---

### Post by jondecker76 on 2008-11-02
My sound is not working - I just upgraded to Intrepid.... I am using an MAudio Delta 1010 card that worked fine in Ubuntu Studio 0704


Upon going to System->Preferences->Sound, and hitting the test button, i get the following error message:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

```

Changing from Autodetect to Pulse Audio yields the same message. Choosing any of the OSS options will yield a static hiss, followed by a similar error message.

Is anyone else having these issues?

---

### Post by leifjonny on 2008-11-02
Problem is your card doesnt work with pulseaudio, solution is here:

[http://ubuntuforums.org/showthread.php?t=963914&highlight=pulseaudio+audiophile]("http://ubuntuforums.org/showthread.php?t=963914&highlight=pulseaudio+audiophile")

---

