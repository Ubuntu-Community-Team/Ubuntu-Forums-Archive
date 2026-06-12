---
title: "Skype audio problems - constant white noise"
date: 2008-11-23
forum: General Help
---

### Post by b3n0 on 2008-11-23
Hey all,

My mates complain that my when I am in the conversation over skype they get white noise and echoes. They have said its like I'm talking to them whilst in the shower. I was told to install ALSA mixer, I have and I've tried adjusting settings, no joy. To add to the problem; when I updated to 8.10, I now get this error. 'problem with audio playback'. Skype can no longer make or receive calls.
[IMG]http://fc74.deviantart.com/fs38/f/2008/327/3/7/SCR02_by_B3N0.png[/IMG]  

Thanks for your help,

---

### Post by pnavarrc on 2008-11-29
Hi,

   Try changing the values in the skype options > sound devices. The configuration must be like this:

Sound In:  **HDA NVidia (hw:NVidia,0)**
Sound Out: **pulse**
Ringing:   **pulse**

The **sound in** device must be *your device*, try with different values in sound in and make the test call. Good luck!

      Pablo.

---

### Post by b3n0 on 2008-11-29
Thanks! That fixed the problem!
I used
Sound In    HDA Intel (hw:Intel,0)
Sound Out   Pulse
Ringing     Pulse
Thanks heaps

---

