---
title: "ALC883 Digital Channel not working"
date: 2008-05-11
forum: Hardware
---

### Post by David Starling on 2008-05-11
I'm very new to Linux/Ubuntu, just installed 8.04, and I can't get the digital channel on my ALC883 onboard audio to work. The analog (in the back and the headphones) works and the OS recognizes my card if I go to System/Preferences/Sound, but I can't get any signal out of the optical or composite digital outs. I've checked the levels in alsamixer and it lists all the surround sound channels. 

I have tried [this]("http://ubuntuforums.org/showthread.php?t=616845&highlight=alc883") and I am considering trying OSS v4.0 instead of ALSA. 

Anyone have any ideas?

---

### Post by chewearn on 2008-05-12
Have you unmute the digital channel in alsa-mixer?  I found that the default behavior (after fresh install) is mute.

Open alsa-mixer, menu > preferences.  Select the checkbox for IEC958.  A new tab should appear in the alsa-mixer main window.  In the tab, there is another checkbox for IEC958.  Select this one, and the digital channel should now be unmuted.

.

---

### Post by David Starling on 2008-05-12
I don't see where you found the "menu -> preferences." When I open alsa-mixer (either via terminal or by installing the gui), there are no menus, just all of the channels and their volume.

---

### Post by David Starling on 2008-05-12
I got it to work. I didn't find the menu, but I was able to "unmute" it through the GUI, just not in terminal. Thanks for your help.

---

### Post by chewearn on 2008-05-12
Oops, I didn't realize there is a terminal version of alsamixer.  Glad it works for you now.

---

