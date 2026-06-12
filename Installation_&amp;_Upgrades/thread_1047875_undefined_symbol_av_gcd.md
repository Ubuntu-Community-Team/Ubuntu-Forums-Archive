---
title: "undefined symbol: av_gcd"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by xzkto on 2009-01-22
Good evening. I tried to install ffmpeg from the latest svn and messed some thing up. Now i get this error : 

ffmpeg: symbol lookup error: /usr/local/lib/libavcodec.so.52: undefined symbol: av_gcd

when i try to use ffmpeg. I tried to purge/reinstall ffmpeg libavcodec libavutil and some more, tried to rm all libavcodec.so/.a files then "sudo make install" again. but nothing changed. Google shows nearly nothing for "av_gcd", so i just dont know where to look. How can i find in what library this function is defined? Any ideas how to fix this? Thx in advance. And sorry for bad english.

---

### Post by FakeOutdoorsman on 2009-01-23
Your English is fine.  Try removing ffmpeg and then follow these instructions:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by xzkto on 2009-01-23
Thx a lot. That fixed it. The manual is great, but you have to copy libx264.so.66 from /usr/local/lib/ to /lib/ or to the place, where you keep your libraries. But can anyone tell me, is there any way i can search for a library, that will let me use the function i want (for future problems)?

---

