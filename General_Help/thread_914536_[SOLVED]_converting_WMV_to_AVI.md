---
title: "[SOLVED] converting WMV to AVI?"
date: 2008-09-08
forum: General Help
---

### Post by cowboyup6983 on 2008-09-08
can anyone think of some simple apps both for linux or windows that let you convert WMV to AVI format?

prefer windows but ubuntu works fine too.

---

### Post by shirilover on 2008-09-08
For either there is avidemux.
In windows, you can use avisynth/virtualdub

---

### Post by Samhain13 on 2008-09-08
Install ffmpeg from the repositories.
(I'd recommend the one from Medibuntu though.)

Then, in the command line:
```

cd /directory_where_the_wmv_is
ffmpeg -i thewmvfile.wmv thenewfile.avi

```
...wait a bit, and you'll get a new .avi file.

Do a search for ffmpeg or "man ffmpeg" to find out about its options.

---

### Post by mb_webguy on 2008-09-08
Avidemux is probably the simplest GUI solution.  Just open the file, change the audio, video, and container drop-down boxes on the left to whatever you like, then click save.

You can also use VLC to transcode any format it can play (which is most of them) to any other format it can play.  Just open the file and then go to File->Wizard, select the transcode option, and then provide the appropriate information in the next few steps.

---

### Post by cowboyup6983 on 2008-09-08
cool thats everyone!

---

