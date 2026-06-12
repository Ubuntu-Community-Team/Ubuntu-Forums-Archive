---
title: "Hauppauge 950Q Audio and Video"
date: 2009-12-31
forum: Hardware
---

### Post by buntunub on 2009-12-31
This is a nifty little usb tv stick that works very well in Windows (xp, vista, and 7). Video is outstanding in Linux on Tvtime. Audio is the issue and remains so, however, there are some workarounds.

Threads [here]("http://www.kernellabs.com/blog/?p=296&cpage=1#comment-914"), [here]("http://ubuntuforums.org/showthread.php?t=1332986&highlight=950Q"), [here]("http://ubuntuforums.org/showthread.php?t=1230531&highlight=950Q"), and [here]("http://ubuntuforums.org/showthread.php?t=1284056&highlight=950Q").

All of these threads bear useful ideas and rather than repeat them, I will just post what has worked for me. I have not tried to setup Mythtv with it due to my unusual setup. My script -

```
#!/bin/sh
nice -n 0 | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay – Dplug:hdmi & tvtime -M -g 1500×800 -I 800;
wait 1 tvtime
killall arecord;
killall tvtime 
```

To get this working I compiled the latest and greatest v4l drivers (Mercurial), extracted the latest firmware (dvb-fe-xc5000-1.6.114.fw) all of which can be done by following the above links or using wiki's - only took a minute or three. This is still a work in progress, and this is mine so far. Please help and post your solutions and current work here to keep this thread current and help all.

---

### Post by buntunub on 2009-12-31
Ok, a little more mucking about on this has yielded some awesome results now, at least for me. Checking out [this]("http://ubuntuforums.org/showthread.php?t=1320515&page=2") thread gave me some ideas about how to setup tvtime a little more sensibly for my hardware. Script as follows.

```
#bin/sh
nice -n 0 | arecord -D hw:1,0 -f S16_LE -c2 -r48000 | aplay - & tvtime -M -g 1400x790 -I 850 -s .1;
killall arecord;
killall tvtime
```

*nice assigns a higher priority (man nice)

*arecord/aplay pipes the audio from the 950Q through.

-- hw:1,0 is how my hardware is setup as per dmesg, lspci, lsusb, cat /proc/snd, etc.

-- -f S16-LE -c2 -r48000 as per man arecord - > Sample format Recognized sample formats are:  S8  U8  S16_LE  S16_BE  U16_LE  U16_BE  S24_LE S24_BE U24_LE U24_BE S32_LE S32_BE U32_LE U32_BE FLOAT_LE FLOAT_BE FLOAT64_LE FLOAT64_BE IEC958_SUBFRAME_LE IEC958_SUBFRAME_BE MU_LAW A_LAW IMA_ADPCM MPEG GSM. Some of these may not be available on selected hardware. There are also two format shortcuts available:
              -f cd (16 bit little endian, 44100, stereo [-f S16_LE -c2 -r44100]
              -f dat (16 bit little endian, 48000, stereo) [-f S16_LE -c2 -r48000]
              If no format is given U8 is used.

-- (man aplay) aplay with no options seems to have really done the trick for me here. Lucky me! I went through first and made sure all my sound hardware, pulse audio, etc were properly setup first and that is more important than anything else!

-- (man tvtime) tvtime -M (windowed mode) -g (geometry) -I (input scan width*) -s (delay, required in my case because audio was just a tad offset from the video)

*man tvtime -I = > V4L input scanline sampling (defaults to 720. This sets how many pixels per scanline to request from the capture card.  A higher setting gives better  quality, while a lower  setting  means  we do less work, and so tvtime will run faster. If you have a slower CPU (like, less than 500Mhz or so), maybe values of 480 or 400 might suit you best.  For best quality, choose a high value like 720 or 768.  Many capture cards cannot sample higher than 768 pixels per scanline.

---

### Post by buntunub on 2009-12-31
[attach]141940[/attach]

[attach]141941[/attach]

---

### Post by buntunub on 2010-01-04
Ok, much more mucking around with this thing has left me a pretty good headache and I think im done with it for now. The above tvtime script is really good and works well for a long time before the arecord/aplay stream drops out of sync and you lose it eventually. A simple restart fixes this, but its still a pain. I think the only real solution is to get both audio and video working 100%. I finally accomplished this with the following script:


```
#bin/sh
mplayer -tv driver=v4l2:input=0:device=/dev/video0:norm=NTSC:chanlist=us-cable:adevice=hw.1:audiorate=48000:immediatemode=0:adevice=/dev/dsp1:amode=1:outfmt=411p tv://~/.mplayer/channels.conf -geometry 1200x700 -monitoraspect 16:9 -stop-xscreensaver -vo vdpau:sharpen=0:deint=4:pullup
```

This gets me fully sync'd audio and video (much better video out than tvtime). The limitations to this is that you have to manually setup your channels via mplayer -tvscan autostart, then fix up your channles.conf file so that it meets your needs later. I kept a copy of the mplayer man page handy while spending a couple days playing around with different options and voila! This script will work if you have the exact same hardware as I do. If you dont, then it wont work without some tweaking, but you can eventually get it to work with a bit of playing. This was done on Kubuntu Karmic using the default pulseaudio setup on an HP6214y with an Nvidia GTS250 card so this system can handle pretty much any type of encoding/decoding options I throw at it with ease. Your mileage may vary, but for sure I can report that the 950Q does operate with full functionality and with fantastic video quality.

If your using this tuner with slimmer hardware, I recommend working from a minimal mplayer setup and build up options from there. Something like:

> mplayer -tv driver=v4l2:input=0:device=/dev/video0:norm=NTSC:chanlist=us-cable:adevice=hw.1:audiorate=48000:immediatemode=0:adevice=/dev/dsp1:amode=1 -tvscan autostart tv:// -stop-xscreensaver

Change values for your hardware. This should at least get you going. Take the output from the tvscan and paste it into the ~/.mplayer/channels.conf file, then remove the tvscan option in future launches and specify the channels.conf as I did above and then all you have to do to change channels is use the k and h keys.

---

### Post by buntunub on 2010-02-16
Hi. A little follow up. This thing is still working great using the above Mplayer script. 

For those of you who are still struggling to get the 950Q working, I definitely sympathize! This was the result of a whole weekend spent studying the Mplayer man pages, experimenting with the litterally dozens of command line options and tweaks until finally - success! Start with just trying to get video working (easy), then work in options to get your sound system working (not so easy), then continue to message it with more options (buffers) until you get video and audio in sync with awesome picture quality. It takes a long long time, and I am sure I could continue to tweak it even more for a better output. It never ends :p

The good news is that it definitely does work - and work very well - via Mplayer. Keep on trying, the results are definitely worth the trouble.

---

### Post by buntunub on 2010-02-16
Here is my latest Kubuntu 9.10 desktop with Mplayer running the 950Q.

---

### Post by buntunub on 2010-05-20
Update to this thread.

In Lucid this seems to work ootb in tvtime, but sound can still be a tad spotty, depending on your hardware. In my case, I manually upgraded ALSA to 1.0.23, updated the driver list, and now all works perfectly in tvtime with perfectly sync'd sound, no scratchiness or ringing. The mplayer script above still works flawlessly as well, and with vdpau, which tvtime can not do.

---

