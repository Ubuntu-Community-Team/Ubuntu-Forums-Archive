---
title: "Laggy MPlayer audio and a crash"
date: 2005-12-05
forum: General Help
---

### Post by duminas on 2005-12-05
First off, I built this myself--didn't install out of the repositories, since the **mplayer-k6** in there had a couple problems on my system--fonts didn't install and it considered "Fullscreen" to mean "same video size, just black borders around it taking up the whole screen". Refusing to play half of my library even after sticking files in /usr/lib/win32 is *not* nice when they worked on Hoary. I am also using alsa, though ESD does the same things.

After building it, the lagging sound in certain video persists.
Specifically, this error is shown at the start of playback of all video files which have an MP3 audio stream:
> Requested audio codec family [mad] (afm=libmad) not available. Enable it at compiliation.And yet, even so the audio plays (the video window appears below the error), it's just lagged a bit behind the video, which is especially noticable when I jump around within the video.

The version of mplayer I'm using is 1.0pre7try2. Compiled as such, using [this](http://www.ubuntuforums.org/showthread.php?t=31061&page=1&pp=10) guide to assist me (aside from having to export GCC):
```
export GCC=3.3; ./configure --enable-gui
```
As it told me to try enabling mad in the compilation, I went back and did a:
```
./configure --help
```
On it to see what options were available. Lo-and-behold, there is a **  --with-madlibdir=DIR ____ libmad (libmad shared library) in DIR** option. However, I do not know where the libmad files are, which is part of the question.

What would be causing the laggy MP3 audio, and how should I go about fixing it?

As to the crash I mentioned in the title, whenever an OGM file finishes playing, I get this on the terminal:
```
[ws] Error in display.
[ws]  Error code: 13 ( BadGC (invalid GC parameter) )
[ws]  Request code: 146
[ws]  Minor code: 3
[ws]  Modules: (NULL)
```
Any idea about that one?

Thanks, guys.

---

### Post by pizzach on 2005-12-17
Answering some of the quick and easy questions:

If your going to install by mand, I put my w32 files in two directories:
/usr/local/lib/codecs
/usr/lib/codecs

Have you tried searching for libmad in Synaptic Package Manager?  Usually installing the dev version takes care of the compile problems.  You can also get the source by search in google for "name_of_what_you_are_looking_for project" or "name_of_what_you_are_looking_for sourceforge"  I would be surprised though that "sudo apt-get build-dep mplayer" didn't get all of that stuff for you.  Though it hasn't been working for me for mplayer lately for some reason.

Search for a thread called the "ultimate mplayer config" for configureation file suggestions. A number of your problems look like they stem from lack of configuration.  "like zoom=1"

---

### Post by kaamos on 2005-12-17
[QUOTE=duminas]First off, I built this myself--didn't install out of the repositories, since the **mplayer-k6** in there had a couple problems on my system--fonts didn't install and it considered "Fullscreen" to mean "same video size, just black borders around it taking up the whole screen".[/QUOTE]

Did you ever check if you used the xv video-output? This is generally caused by using x11.

---

