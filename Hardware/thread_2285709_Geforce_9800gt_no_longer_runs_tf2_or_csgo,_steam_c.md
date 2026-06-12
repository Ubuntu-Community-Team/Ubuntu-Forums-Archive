---
title: "Geforce 9800gt no longer runs tf2 or csgo, steam claims my opengl is outdated."
date: 2015-07-08
forum: Hardware
---

### Post by kylesmail80 on 2015-07-08
I recently got Ubuntu 14.04 after my windows trial expired and the first thing I did was install steam and then TF2. The game originally launched perfectly fine and I was able to join a game, but my fps was terrible (30 fps instead of the 110 I'd get in windows). So I went into the additional drivers tab and started changing the drivers. I launched the game again and it ran at roughly 60 fps, which I guess was fine. I then exited the game and shut down my computer.I turned on my computer and tried to launch TF2, I got this error: "Could not find required OpenGL entry point 'glGetError'! Either your   video card is unsupported, or you OpenGl driver needs to be updated." Then when I tried to launch csgo (for the first time) I got this error: "Could not find required OpenGL entry point 'glColorMaskIndexedEXT'!  Either your video card is unsupported, or your OpenGL driver needs to be  updated." When looking in the terminal I launched steam it claimed my driver was outdated, but after running ```
/home/kyle# glxinfo | grep "OpenGL version"
``` It said I had this driver and version: ```
string: 2.1.2 NVIDIA 340.76
``` Which Is perfectly up to date to run steam games is it not? when looking into the steam terminal it claimed I had version 1.3.0 and that I need at least 2.0.0, which I have. What can I do to get tf2 and csgo working again?

---

