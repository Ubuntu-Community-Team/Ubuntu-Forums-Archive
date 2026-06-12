---
title: "Help! GUI gone!"
date: 2008-11-14
forum: General Help
---

### Post by mcphatty on 2008-11-14
I'm not quite sure what happened, but after installing two updates and fixing my sound issue, ihave no GUI. The updates were passwrd and login, and for the sound I ran apt-get --purge linux-sound-base  alsa-base alsa-utils and then reinstalled the same thing. I reboot and now I'm stuck in terminal. What do I do? I'm posting this from my phone, thankfully I still have that!

---

### Post by adult swim on 2008-11-14
try ```
startx
``` from the terminal

---

### Post by mcphatty on 2008-11-14
okay, that worked. what happened though? did i just experience this part of the sound solution guide?

> 
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following

sudo apt-get install gdm ubuntu-desktop


---

