---
title: "Multiple versions of the same program"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by nolanpro on 2009-05-20
I have a very customised/patched version of FFMpeg that I use often and compiled from source, but because of its patchwork, some features don't work right.

I'd like to keep it but also install a nice, clean, stable version (like what I would get from #sudo apt-get install ffmpeg).

Does anyone know how I can do this without overwriting anything? I'm good with putting it in a different folder, maybe under my home dir, and aliasing it from /usr/bin so I could call it ffmpeg2.

Or, I'm also ok with calling it from its root path like /home/me/clean-ffmpeg/ffmpeg [opt....]

Thanks!

---

### Post by FakeOutdoorsman on 2009-05-24
Did you try using checkinstall with your compiled FFmpeg?  This will create a "clean" install.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

