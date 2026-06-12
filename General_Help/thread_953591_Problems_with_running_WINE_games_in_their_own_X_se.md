---
title: "Problems with running WINE games in their own X server"
date: 2008-10-20
forum: General Help
---

### Post by Drakim on 2008-10-20
I'm using Ubuntu AMD64, but I don't think this problem is related to that. Forgive me if I should have posted in that forum anyway, I wasn't quite sure.

I'm trying to make Starcraft work better in Wine. I have it running nicely in windowed mode, but it's just so darn small. But then I stumbled upon this:

[http://ubuntuforums.org/showthread.php?t=751863](http://ubuntuforums.org/showthread.php?t=751863)

Which seemed like my solution. I tried running:

"startx /usr/bin/wine /home/drakim/StarCraft.exe -- :1"
(no, I don't have such an ugly game app structure, I chanaged the path to make it more readable for you :o)

And it semi-works.

I have a TwinView dual screen setup, configured using the nvidia-settings tool. I've had some fullscreen problems, but solved that by running all my games in windowed mode at the size of one of my screens.

I believed however, that by using a completely new X server for Starcraft, these fullscreen problems would not apply.

As it is now, when I run that line, Starcraft starts, but my screens retain their 1280x1024 resolution, and the Starcraft window is positioned in the top left corner, covering 800x600 of my left monitor. The rest of the screens is filled with a pattern of some sort (every other pixel black and white). I tried to take a screenshot, but realized that since it's a diffrent x server, it won't work. heh.

I know I'm starting a new x server properly. I get to see the nvidia logo a second or two before Starcraft starts.

Now, what am I doing wrong? D:

---

### Post by Drakim on 2008-10-20
Woot!

I solved it somehow!

It was pure guesswork though (still new to Linux).

In my xorg.config file, I simply applied the following metamodes:

```
Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL;"
```

And the xstart command magically picks the right one, giving me perfect fullscreen.

Hope this helps other people for reference.

---

