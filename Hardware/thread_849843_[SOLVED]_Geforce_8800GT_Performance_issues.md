---
title: "[SOLVED] Geforce 8800GT Performance issues?"
date: 2008-07-04
forum: Hardware
---

### Post by Victormd on 2008-07-04
I've read several threads on people having issues with graphics card resolution but not so much performance.

I have a NVIDIA Geforce 8800GT and it's installed properly, with the latest driver, compiz works fine but I've read about people getting 10k+ frames per second on glxgears but this is what I get:
> 
302 frames in 5.0 seconds = 60.270 FPS
300 frames in 5.0 seconds = 59.885 FPS
300 frames in 5.0 seconds = 59.884 FPS
300 frames in 5.0 seconds = 59.887 FPS

Anyone have any idea why?

---

### Post by Victormd on 2008-07-05
I've actually asked this on several open threads but never got a response... any 8800GT owners with the same issue? Or is this actually normal?

---

### Post by phidia on 2008-07-05
Those rates do seem low but glxgears isn't an accurate fps measurement tool.
See [this]("http://www.nvnews.net/vbulletin/showthread.php?t=105075") from nvnews, an analysis of [graphic card performance]("http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS") on wiki, this thread [here]("http://ubuntuforums.org/showthread.php?t=848733&highlight=Geforce+8800GT") and the ubuntu community [howto]("https://help.ubuntu.com/community/Video").

---

### Post by sdennie on 2008-07-05
Those glxgears numbers just mean that you have sync to vblank enabled somewhere.  Probably in compiz.  You can disable it for your testing but, in my experience compiz looks much nicer with sync to vblank on.  To disable:

```

sudo apt-get install compizconfig-settings-manager

```

System->Preferences->Advanced Desktop Effects->General Options->Display Settings and disable sync to vblank for your tests.

---

### Post by Victormd on 2008-07-05
That did the trick. I also think compiz looks nicer with sync to vblank on and I'm going to keep it on.

Basically, I just wanted to know/check if there was something wrong with my graphics card install, and after testing with vblank turned off, I can say that there isn't! :)
Thanks

---

