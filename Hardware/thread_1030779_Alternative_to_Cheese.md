---
title: "Alternative to Cheese?"
date: 2009-01-04
forum: Hardware
---

### Post by ECas123 on 2009-01-04
Alright, so apperently Cheese doesn't work with webcams that use uvcvideo which is what my Crystal Eye webcam uses. So does anyone know of a program that does what Cheese does for video (all I want to do is record video w/ audio and save it as avi) any suggestions?

---

### Post by symon1980 on 2010-02-02
lol
I see nobody has replied to your post... dunno if you've solved 
your problem by now, but 1 suggestion is to install mplayer

then... use mencoder in the command line to record video/sound as an avi...

here is an example

mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video1:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o video.avi


you may have to adjust the video or sound device... in this instance i have used /dev/dsp1 for audio but you might have to try /dev/dsp

and for video i have used /dev/video1      if that don't work try 
/dev/video0     or /dev/video2

it will start recording although you won't see anything.. just a bunch of jibberish in the konsole.... once you stop it by pressing "q" it will put the video.avi file in your home directory


hope this helps anybody

ps, an alternative is to install ffmpeg     "sudo apt-get install ffmpeg"

and use this command in the terminal instead of mencoder

ffmpeg -f oss -i /dev/dsp -f video4linux2 -s 320x240 -i /dev/video0 out.mpg


again, adjusting device to suit your setup.... could be video0   video1    even video2     try them all until it works.
cheers


kaddy

---

### Post by no2498 on 2010-02-02
unless you have a 64 bit computer do not do his
open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2 click the bottom test at each try
and try ( wxcam ) or get it

---

### Post by Digikid on 2010-02-02
So nothing simpler?  LOL!!!!!!!!

---

### Post by gareththomasnz on 2010-12-20
> **no2498 said:**
> unless you have a 64 bit computer do not do his
open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2 click the bottom test at each try
and try ( wxcam ) or get it

Finally somebody that knows what they are talking about.

I think more poop has been posted about ubuntu and webcams than anything else.

This fixed my cheese problem

---

### Post by IcarusR on 2010-12-20
> I think more poop has been posted about ubuntu and webcams than anything else.


Yep, including the sweeping statement from the OP

```
apparently Cheese doesn't work with webcams that use uvcvideo
```

I have webcam that uses uvcvideo that works fine with cheese !!

---

### Post by Calerid on 2011-11-11
> **IcarusR said:**
> Yep, including the sweeping statement from the OP

```
apparently Cheese doesn't work with webcams that use uvcvideo
```I have webcam that uses uvcvideo that works fine with cheese !!

Umm I thought cheese only used the UVC drivers?

---

### Post by coldraven on 2011-11-11
Get uvcview from the Software Centre.

"guvcview is a simple GTK+ interface for capturing and viewing video from devices supported by the Linux UVC driver."

---

### Post by IWantFroyo on 2011-11-11
If you're going to record videos, guvcview would probably be better for you. Unless they changed something, Cheese just takes pictures.

Edit: Thread necromancy? Oops.

---

