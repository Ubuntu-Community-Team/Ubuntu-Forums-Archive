---
title: "Cutom Login Sounds"
date: 2008-09-16
forum: General Help
---

### Post by Valok on 2008-09-16
So I'm just back into Linux after a long hiatus, and admittedly I'm not very familiar with how things work, but I get by through exploring and asking questions.  So here I am!

I want to put a song clip as my login sound.  Originally it wouldn't work because the song was in MP3 format, and Ubuntu wants a .wav format only.  So I renamed the file to .wav instead of .mp3.  That let me select the sound as my login tone, but it won't play.

The clip plays through all my other media players, just not when I login.  Any help would be greatly appreciated, thanks!

---

### Post by ryanhaigh on 2008-09-16
You will probably have to convert the mp3 to a proper wave file. Changing the extension of the filename doesn't really do anything. Your media players look at the contents of the file to determine that it is an mp3.

There are a number of tools which you can use to properly convert the mp3 to a wave file but possibly the easiest is [apt://nautilus-script-audio-convert]("apt://nautilus-script-audio-convert") which integrates with the nautilus file manager. You simply right click on your audio file go to scripts and convert the file to wave format.

---

### Post by Valok on 2008-09-17
Awesome!  Thanks for the point in the right direction.  I'll give this a go once I get home and let you know how it went.

---

### Post by Valok on 2008-09-17
Hmm, this didn't seem to work for me.  Once I installed the package you linked, there is no additional option to change the file type or convert it.

---

### Post by ryanhaigh on 2008-09-17
You will need to restart nautilus for the change to take effect, you can either do this by running nautilus -q then starting nautilus again (just open something from the places menu), or you can just logout and back in.

---

### Post by Valok on 2008-09-18
Even after logging in and logging out I still don't see the option.  Do I need to start up the program or anything?  Or should it just work after installing it.  If so maybe I should try restarting completely, or finding another program.

---

