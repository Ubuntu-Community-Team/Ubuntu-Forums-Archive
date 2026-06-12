---
title: "[SOLVED] Sound Completely Dead"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by Roanoke on 2008-03-05
Simply, any and all sound emanating from ubuntu is totally dead. I have no Idea what to do. I have logged out and rebooted, with no luck.

---

### Post by Roanoke on 2008-03-07
Can anyone please help?
Here are my sound settings.

---

### Post by Bubba64 on 2008-03-07
here is a post that lists codecs and addon stuff that should make everything work hopefully the sound settings can be part of the problem, but not knowing what types of sound your not getting, makes it difficult to find an answer install the extras to get started.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Also install alsa-oss in synaptic and the gstreamer extras in add remove.

---

### Post by Roanoke on 2008-03-07
I'm not getting any sound, but I'll have a look through that, thanks,

---

### Post by Roanoke on 2008-03-07
Nope, installed everything except for the ripping/burning and the firefox plugin, and sound doesn't work. However, the system beep works, and sound doesn't work in any other account.

---

### Post by Roanoke on 2008-03-10
Come on, no one can help me?

---

### Post by 4l13n666 on 2008-03-11
Can you please post the result of lspci -v, and lspci (put these commands in the terminal). Are you sure that your sound card is detected and unmuted? Open your terminal and run alsamixer, and check if anything is muted.

---

### Post by Roanoke on 2008-03-11
Thanks for helping me. Attached is a script of my terminal output and my alsamixer settings.

---

### Post by 4l13n666 on 2008-03-12
Alright.

The following link helped me to get my sound working and since you are using intel drivers, it may help you too.

[http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)

If this link helped you, let me know! :)

---

### Post by superprash2003 on 2008-03-12
this might help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Roanoke on 2008-03-12
@4l13n666: 404 Error.
@Supersplash: Tried that, didn't work.

---

### Post by Roanoke on 2008-03-15
Here's how I got it working:

Visited
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
Did what it told me.

Then I opened the volume control window, unmuted everything and brought the volume up.

---

