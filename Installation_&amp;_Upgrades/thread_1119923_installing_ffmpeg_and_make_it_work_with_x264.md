---
title: "installing ffmpeg and make it work with x264"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by kakarala on 2009-04-08
hi
 I am trying to install ffmpeg and encode using x264.I installed x264 first and i downloaded ffmpeg and configured and when make command is given it gives following error

libavcodec/x86/dsputil_mmx.c: In function ‘transpose4x4’:
libavcodec/x86/dsputil_mmx.c:699: error: can't find a register in class ‘GENERAL_REGS’ while reloading ‘asm’
libavcodec/x86/dsputil_mmx.c:699: error: ‘asm’ operand has impossible constraints
make: *** [libavcodec/x86/dsputil_mmx.o] Error 1

---

### Post by FakeOutdoorsman on 2009-04-08
These tutorials may be of use.  The first one explains how to compile FFmpeg and x264, and the second explains how to enable restricted encoders in FFmpeg from the repository.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

---

### Post by kakarala on 2009-04-09
i installed using the tutorial and it gives same error after configuring

after downloading i configured using the command
 
./configure --enable-gpl --enable-libx264 --enable-swscale --enable-debug --disable-optimizations --disable-stripping

after when i am installing it gives same error

---

### Post by FakeOutdoorsman on 2009-04-09
> **kakarala said:**
> i installed using the tutorial and it gives same error after configuring

after downloading i configured using the command
 
```
./configure --enable-gpl --enable-libx264 --enable-swscale --enable-debug --disable-optimizations --disable-stripping
```

after when i am installing it gives same error

The option *--enable-swscale* is depreciated with the recent SVN, so it is no longer a valid option.  The *--disable-optimizations* option is your troublemaker I think, but I have no experience with it.  Ask on the #ffmpeg IRC channel or on the [ffmpeg-user mailing list](http://ffmpeg.org/contact.html).  You could also just not use that option.  Why do you want to disable optimizations?

---

### Post by kakarala on 2009-04-10
thanx for help i removed both the commands and it worked properly
 
but i captured the video from webcam and saved as local file.when i am trying to play using ffplay it gives error saying
 
The program 'ffplay' is currently not installed.  You can install it by typing:
sudo apt-get install ffmpeg
bash: ffplay: command not found

---

### Post by FakeOutdoorsman on 2009-04-10
You missed the "Optional Dependencies" section in the guide:
[indent]**libsdl1.2-dev**: Required for FFplay, a simple media player using the FFmpeg libraries and the SDL library.[/indent]
You will need to install this package and then uninstall FFmpeg, make distclean, reconfigure FFmpeg, and then finally reinstall FFmpeg.  Refer to the "Updating Your Installation" section of the guide.  I also suggest using the provided FFmpeg configuration options shown in the guide for better usability.

---

### Post by kakarala on 2009-04-10
thanx for help i am able to encode and decode the video but can we encode and play the video at same time for the webcam

---

### Post by FakeOutdoorsman on 2009-04-10
Yes, if you use a suitable output such as mpg.  I think you would have to wait for everything to encode first if you're using libx264.  I was able to simultaneously encode to mpg and play that output with FFplay.

---

