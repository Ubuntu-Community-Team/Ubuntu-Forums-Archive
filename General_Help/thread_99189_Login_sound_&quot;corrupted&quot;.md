---
title: "Login sound &quot;corrupted&quot;"
date: 2005-12-05
forum: General Help
---

### Post by linbetwin on 2005-12-05
I noticed in the last few days that the login music sounds strange, as if it were corrupted. I don't know how to describe it, but it's something like a trembling...

I also noticed (to my surprise) that in /usr/share/sounds I have startup.wav and startup3.wav, as well as shutdown.wav and shutdown1.wav. Why are there copies of these files and why the gates are they WAV files? Yes, I did install the w32codecs, but I didn't convert anything to wav!

---

### Post by Sutekh on 2005-12-05
[QUOTE=linbetwin]I noticed in the last few days that the login music sounds strange, as if it were corrupted. I don't know how to describe it, but it's something like a trembling...

I also noticed (to my surprise) that in /usr/share/sounds I have startup.wav and startup3.wav, as well as shutdown.wav and shutdown1.wav. Why are there copies of these files and why the gates are they WAV files? Yes, I did install the w32codecs, but I didn't convert anything to wav![/QUOTE]

I have startup.wav, startup3.wav, shutdown.wav, shutdown1.wav.  The ~1.wav and ~3.wav are actually links to the actual .wav files.  Check it out for yourself.

They were .wav files before I installed W32 codecs, so I guess .wav isn't proprietary.  I think IBM and Microsoft worked together on .wav.  I'm sure someone had a more complete answer on that.

Don't know why your sounds would sound trembling... that's another kettle of fish...

---

### Post by linbetwin on 2005-12-05
[quote=Sutekh]I have startup.wav, startup3.wav, shutdown.wav, shutdown1.wav. The ~1.wav and ~3.wav are actually links to the actual .wav files. Check it out for yourself.

They were .wav files before I installed W32 codecs, so I guess .wav isn't proprietary. I think IBM and Microsoft worked together on .wav. I'm sure someone had a more complete answer on that.

Don't know why your sounds would sound trembling... that's another kettle of fish...[/quote]

Thank you. I would post the file, but it's 1.9 MB in size.

---

### Post by Sutekh on 2005-12-05
[QUOTE=linbetwin]Thank you. I would post the file, but it's 1.9 MB in size.[/QUOTE]

I was going to say I could always post mine.  Try the compressed attachments.  How does the rest of your system sound??

**Edit:**  Gonna need two posts :-\".  Nah doesn't like it.

---

### Post by linbetwin on 2005-12-05
[quote=Sutekh]I was going to say I could always post mine. Try the compressed attachments. How does the rest of your system sound??

**Edit:**  Gonna need two posts :-\".  Nah doesn't like it.[/quote]

I fixed the problem! The PCM volume was turned up at maximum. You can try it yourself to reproduce my "bug": slide the PCM volume at max in the playback tab of the Volume control and play the startup wav file.

---

