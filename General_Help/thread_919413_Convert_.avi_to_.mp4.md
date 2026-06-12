---
title: "Convert .avi to .mp4"
date: 2008-09-14
forum: General Help
---

### Post by fedex1993 on 2008-09-14
Yes i have some .avi files that i would like to convert to .mp4 files. MY question is there a program out there that can do this? Or another video format that i can add to my ipod. Thanks.

---

### Post by mb_webguy on 2008-09-14
Converting files with Avidemux ("sudo apt-get install avidemux") is fairly painless.  Just open the file in Avidemux, select the video codec, audio codec, and container from the drop-down controls on the left and click Save.

---

### Post by fedex1993 on 2008-09-14
> **mb_webguy said:**
> Converting files with Avidemux ("sudo apt-get install avidemux") is fairly painless.  Just open the file in Avidemux, select the video codec, audio codec, and container from the drop-down controls on the left and click Save.

avidemux seemed to make it very very very choppy video.

---

### Post by SuperSonic4 on 2008-09-14
winFF could work for you although I don't think it is in the repos so you'll have to google it. It is a front-end for FFmpeg which you might want to check you have, especially is avidemux is choppy.

---

### Post by fedex1993 on 2008-09-14
> **SuperSonic4 said:**
> winFF could work for you although I don't think it is in the repos so you'll have to google it. It is a front-end for FFmpeg which you might want to check you have, especially is avidemux is choppy.

well after i redid the frames and what not it was fine. The question is how exactly to i convert the file over to mp4?

---

### Post by mb_webguy on 2008-09-14
SuperSonic4 has a good point that you should have FFMpeg, and not just the one in the normal repositories but the one from Medibuntu.  Follow [these instructions]("https://help.ubuntu.com/community/Medibuntu") to enable the Medibuntu repositories and install the goodies, and make sure you install ffmpeg.  Also, since you're working with mp4 files, make sure you have the x264 and faac packages installed.

To convert the file using Avidemux, all you should have to do is open the file to be converted, then on the left select "MPEG-4 AVC (x264)" under Video, "AAC (FAAC)" under Audio, and "MP4" under Format, then click Save, and give it the name and location where you want to save the mp4 file.

EDIT:  I just noticed that you're converting these files for use on your iPod.  You'll also have to use the "Mplayer Resize" video filter to specify the video resolution of your iPod.

---

### Post by ghostdog74 on 2008-09-14
you can convert avi to mp4 using mencoder, ffmpeg
example only
```

ffmpeg -y -i "2.avi" -title "2" -timestamp "2005-09-24 05:59:40" -bitexact -vcodec h264 -coder 1 -g 250 -s 320x240 -r 29.97 -b 384
-bufsize 384 -acodec aac -ac 2 -ar 48000 -ab 48 -f psp "out.MP4"

```

---

### Post by aquamammal on 2008-09-17
I'm trying to do this, but it keeps giving me a 

trouble initializing audio device 

error msg.

Any thoughts?

Thanks.

---

### Post by aquamammal on 2008-09-17
I'm trying to do this, but it keeps giving me a 

trouble initializing audio device 

error msg.

Any thoughts?

Thanks.

---

### Post by swisscow on 2008-09-17
I have had a lot of success following these instructions here

[HTML]http://thomer.com/howtos/ipod_video.html[/HTML]

and here

[HTML]http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html
[/HTML]

---

### Post by FakeOutdoorsman on 2008-09-17
[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

---

