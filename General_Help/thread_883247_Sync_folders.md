---
title: "Sync folders"
date: 2008-08-07
forum: General Help
---

### Post by gardara on 2008-08-07
I have a portable multimedia player (Archos 605) That mounts as a hdd when I connect it to my computer...
The music folder on my computer changes quite a lot, when I download new music, sort artists, etc.
I am wondering if I can sync the music folder that's on my computer with the music folder on my player every time the player is connected?

---

### Post by damoxc on 2008-08-07
You might be able to do this with the new Banshee. I think you can just put a .cant-remember-what-it-is file on the drive and Banshee will detect it as a media player.

Edit: found it, place an empty file called ".is_audio_player" on the device and banshee will treat it as an audio player.

---

### Post by gardara on 2008-08-07
Thanks, I'll take a look at banshee... However it would be great if there is another possible way.. Since I use amaroK and not banshee

---

### Post by damoxc on 2008-08-07
Could try rsync, if you don't mind dipping down to the command line?

There's even gtkrsync which provides a GUI wrapper around it.

---

### Post by gardara on 2008-08-07
> **damoxc said:**
> Could try rsync, if you don't mind dipping down to the command line?

There's even gtkrsync which provides a GUI wrapper around it.

I actually prefer command line most of the time...

I'll take a look at rsync, thanks :)

---

