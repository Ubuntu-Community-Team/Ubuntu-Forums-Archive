---
title: "WMA to MP3 conversion not working"
date: 2008-08-18
forum: General Help
---

### Post by codeking on 2008-08-18
I'm trying to convert a WMA file to MP3 using SoundConverter, but its not working.  I click convert, and it say it successfully did it, but it took less than a second, which to me is a bit to fast.  Then when I open up the mp3 file, I get an error saying theres no data in the stream.  What could be wrong?

---

### Post by DJ_Peng on 2008-08-19
I'm finding that SoundConverter doesn't seem to like WMA's on my system, although others have had success with it. I use a Nautilus Script called Audio Convert from [G-Scripts]("http://g-scripts.sourceforge.net/"). It doesn't keep the tags, but I use EasyTag to re-tag files. This combination has helped me convert hundreds of WMA files I had collected as a Windows user before I saw the light. :)

---

### Post by Vivaldi Gloria on 2008-08-19
Nothing comes closer to foobar2000 (in wine) for converting files.

---

### Post by codeking on 2008-08-19
I installed foobar, but when i tried to convert it it said this: > Could not load info (WMA support requires Windows Media runtime libraries installed) from:
"Z:\media\Windows\Documents and Settings\Owner\My Documents\My Music\Aerosmith\Gold (Disc 1)\15 Janie's Got A Gun.wma"


---

### Post by Vivaldi Gloria on 2008-08-19
> **codeking said:**
> I installed foobar, but when i tried to convert it it said this:

Oops. It looks like foobar dropped the wma plugin with version 0.9. I'll try to find it.

---

### Post by mb_webguy on 2008-08-19
You can use the VLC media player to convert any file it can play (which is most of them) into any other format it can play (which is most of them).  Just open the file you want to convert, then select the Wizard from the File menu and choose to transcode the file.  After that, it's relatively simple (especially if you're familiar with other transcoding applications.  

I've used several different programs for transcoding audio and video files, and while it isn't necessarily the fastest or most fully-featured (which would probably be the CLI combination of mencoder, ffmpeg, transcode), VLC is certainly one of the easiest and most reliable.

---

### Post by Vivaldi Gloria on 2008-08-19
OK. I solved foobar's wma problem. Download Windows Media Lite from

[http://www.free-codecs.com/download/Windows_Media_Lite.htm](http://www.free-codecs.com/download/Windows_Media_Lite.htm)

and install it using wine. In the installation choose the options as in the attached screenshot. Now foobar handles wma files without a problem.

---

### Post by codeking on 2008-08-19
I downloaded the wmlite, now it says its unable to play.

tried VLC player, can't hear anything when I play the file.

I believe this has DRM on it, I downloaded it from rhapsody a while ago.  Does that make a difference?

---

### Post by Vivaldi Gloria on 2008-08-19
> **codeking said:**
> I believe this has DRM on it, I downloaded it from rhapsody a while ago.  Does that make a difference?

Sure it does. Sorry but I hardly know anything about DRMed files. No idea how they are played.

---

### Post by mb_webguy on 2008-08-19
Yeeeaahh.... You're going to have a problem converting any DRM'ed file, no matter what program you use.  That's sort of the point of DRM, that you can't do what you want with your own property.

---

