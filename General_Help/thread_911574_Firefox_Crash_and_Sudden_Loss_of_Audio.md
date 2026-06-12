---
title: "Firefox Crash and Sudden Loss of Audio"
date: 2008-09-05
forum: General Help
---

### Post by Sharka on 2008-09-05
I am on Ubuntu Hardy Heron.

I added the No Script Addon and proceeded to delete it. Ever since then, I have lost all audio: DVD, Youtube, and streaming radio using MPlayer. Youtube/DVDs are all playing but no sound.

Under my Sounds Preferences, all of them are set to OSS-Open Sound System. When I make a test, I get a message: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.



My Firefox is also now crashing. Could this be related to adding the NoScript addon ? How can I get back my audio ?

Thanks

---

### Post by wolfen69 on 2008-09-05
try ```
sudo apt-get install libflashsupport
``` then restart firefox

---

### Post by Sharka on 2008-09-05
Wolfen69,

It worked. I had to force quit Firefox.  My system froze after I hit the restart button and forced the shutdown by pressing down on the power button.

As a new user, your help is greatly appreciated and only reinforces my commitment to Ubuntu.

Many thanks & have a wonderful weekend !

---

