---
title: "Sound card not sharing more than one application"
date: 2008-09-10
forum: General Help
---

### Post by cmani on 2008-09-10
Hi,
I recently installed Ubuntu 8.04 [Hardy] in my notebook, Seems sound card is not shared between applications either sound card is engaged or not.
Say i watch youtube in firefox 3.0, and open VLC player to listen songs, the VLC player is not giving any sound, until i closes the firefox and restart the vlc player and vice versa.  This situation is not only to firefox and vlc player, any 2 audio/video applications have this issue, while watching youtube, skype riniging is not able to listen.   

Is there any setup to be carried out in my notebook.  I tried some other linux like freespire, puppy it doesn't have such issue.

Pl. advice.

---

### Post by iaculallad on 2008-09-10
> **cmani said:**
> Hi,
I recently installed Ubuntu 8.04 [Hardy] in my notebook, Seems sound card is not shared between applications either sound card is engaged or not.
Say i watch youtube in firefox 3.0, and open VLC player to listen songs, the VLC player is not giving any sound, until i closes the firefox and restart the vlc player and vice versa.  This situation is not only to firefox and vlc player, any 2 audio/video applications have this issue, while watching youtube, skype riniging is not able to listen.   

Is there any setup to be carried out in my notebook.  I tried some other linux like freespire, puppy it doesn't have such issue.

Pl. advice.

Install the sound wrapper for non-free plugin:

```
sudo apt-get install libflashsupport
```

---

### Post by Nepherte on 2008-09-11
It's a pulseaudio problem. You can fix this issue following [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

