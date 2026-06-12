---
title: "No music with Audacious in Fluxbox"
date: 2008-09-23
forum: General Help
---

### Post by orrie on 2008-09-23
I have installed fluxbox on my Ubuntu 8.04, so in the startup I can choose between Fluxbox and GNOME.

The problem is that I can't get audacious to start playing in fluxbox.
But if I tries to play an music-file in VLC it works!
How can I fix this so I can play music in Audacious?

---

### Post by TenPlus1 on 2008-09-23
Silly question, but have you installed the latest version of Audacious from [www.getdeb.net](www.getdeb.net) ?

---

### Post by sizzam on 2008-11-15
I ran into the same problem.   The issue for me was that audacious is set to use pulseaudio by default, but I wasn't starting pulseaudio when I logged into fluxbox.

To resolve the problem, I added  'pulseaudio &'  to my ~/.fluxbox/startup file

---

### Post by orrie on 2009-02-28
If you're going into the preferences and then on "Audio" you will find something says "Current output plugin:" and it's here you can change it.

For me it did work with just changing to OSS Output Plugin or PulseAudio Plugin. (This problems varies if I'm using OSS or PulseAudio by default)

---

### Post by entikryst on 2010-02-25
Thank you so much sizzam!! I'm so glad I found this thread.  I've been struggling with that issue for a long time.

---

