---
title: "[SOLVED] Sound died, and I'm out of ideas"
date: 2008-11-27
forum: General Help
---

### Post by nb1 on 2008-11-27
With Ubuntu 8.10, 32-bit,

I installed a wine 1.1.9 package for Ubuntu and was setting up a game. Everything was working all right, but after running the game a few times while trying to get it working, sound quit working. It's not just for the game, but for all applications. I can't even cat /dev/urandom > /dev/dsp to produce static. I've since removed the wine package, ran an apt-get autoremove, and have rebooted several times but the same problem persists.

The /dev/dsp device still exists, and I have permissions to it. I have a long list of kernel modules loaded with the "snd" prefix. I don't get any errors when trying to play sounds, it's just mute. I've checked the ALSA mixer volume levels, and my sound+speakers are working fine in Windows. Running /etc/init.d/alsa-utils restart seems to successfully restart the server, but still no sound.

I suppose the problem could be something other than wine and windows applications, but I can't think of anything else that changed when the sound quit working. In any case, I'm totally stumped. What should I look for?

Editing since I solved my problem:

Problem was reproducible by changing the audio driver winecfg from ALSA to OSS and back to ALSA again.
The fix for the problem was to run the command "/etc/init.d/alsa-utils reset 0" to reset all ALSA settings back to default.

Useful links:

Comprehensive Sound Problem Solutions Guide
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Alsamixer Restore Default
[http://ubuntuforums.org/showthread.php?t=237096](http://ubuntuforums.org/showthread.php?t=237096)

Thanks everyone.

---

### Post by Peter09 on 2008-11-27
Check your physical hardware and connections / power to it.

---

### Post by philinux on 2008-11-27
Try this

sudo alsa force-reload

---

### Post by nb1 on 2008-11-27
> **Peter09 said:**
> Check your physical hardware and connections / power to it.
As posted, sound works perfectly under Windows, so my speakers and hardware are working properly. I can also get sound when I boot with the Live CD. Something has happened to kill the sound on this installation, and I'm hoping I can fix it rather than start over.

---

### Post by nb1 on 2008-11-27
> **philinux said:**
> Try this

sudo alsa force-reload
It doesn't help. I think all my modules were already loaded. Terminal output is below.
```

...some random stat errors regarding .usbfs and .gvfs...

Unloading ALSA sound driver modules: snd-via82xx snd-via82xx-modem snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-via82xx snd-via82xx-modem snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

---

### Post by philinux on 2008-11-27
Have a look back through your ~/.bash_history file and see if you did anything you can reverse.

Have you got home on it's own partition by the way?

---

### Post by nb1 on 2008-11-27
> **philinux said:**
> Have a look back through your ~/.bashrc file and see if you did anything you can reverse.
I haven't changed anything in .bashrc, do you mean looking at my .bash_history? The only sudo actions I've taken before realizing there was a problem involved mounting ISO images... making a directory to mount to, mounting the image, umounting, removing the directory I had created, etc. This was done so I could install the games.
> Have you got home on it's own partition by the way?
No, I don't... but if you are asking from the idea that I should backup my home directory before doing something (like reinstall), I have other partitions I can make a copy of it to. I'd really like it if I did not have to reinstall Ubuntu to get sound working again.

---

### Post by nb1 on 2008-11-27
I've been digging through various audio troubleshooting guides and finally came across this:
```
/etc/init.d/alsa-utils reset 0
```

Looking at the reset configuration in alsamixer, I had the appropriate ALSA channels turned up all along. I think what happened was, some other channel was enabled, and it conflicted with the proper output channels. I'm not sure how these conflicting channels were turned on to begin with, but the problem seems to be solved now by resetting it to defaults. I feel kind of dumb now, but in any case thank you for trying to help. :)

---

### Post by elbel86 on 2008-11-28
I had the same problem and this solved it quick and easy. Thanks!

---

