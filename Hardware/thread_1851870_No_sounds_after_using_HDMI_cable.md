---
title: "No sounds after using HDMI cable"
date: 2011-09-29
forum: Hardware
---

### Post by yotamoo on 2011-09-29
Hi there
I am using ubunto 10.4 on a lenovo g550 laptop. Everything was ok until I watch a movie using my HDMI cable. I want to output sound to the TV so I went to System -> Preferences -> Sound, then hit the 'Hardware' tab and set it to Digital Stereo (HDMI) ouput and it worked. Problems is now I have no sound output at all. There's only 6 options under 'Hardware' and I've tried them all.

Any ideas? thanks!

---

### Post by arthurzennig on 2012-06-08
It is maybe too late to answer this question, but i was having the same problem here.
I found this post:
[http://ubuntuforums.org/showthread.php?t=1924508](http://ubuntuforums.org/showthread.php?t=1924508)

and the answer, for 12.04 was:

> I think I may have solved the issue. Upon examining  /etc/modprobe.d/alsa-base.conf, I noticed that it no longer had the  following line.

options snd-hda-intel model=auto

I re-added this line, saved, rebooted, and everything seems to be working now.

It seems to have worked for others, but still not for me...
I will keep trying here, if something else works, i let you know.

---

### Post by arthurzennig on 2012-06-08
It seemed that none solution from posts were working for me.
After everything fails, any solution is good, right?
So i did this ( and worked ):
- I plugged back my notebook to the HDMI connection from my turned on tv;
At this moment, i arranged to make the display to show on the tv ( like everytime when i want to watch a movie from the pc in my tv );

- Then, i played a music.
- The sound came from the tv;
- Opened the [I]sound settings;
[/I]- Changed configurations so that the music came from the notebook again;
- unplugged the HDMI cable from the notebook;

**And now i am hearing musics back from my notebook again!** 

footnote: this is no fancy solution and i wish i had one, but it worked right. Now every time when i watch a movie from the notebook through the tv, i will re-adjust the sound configuration to playback from the notebook before i unplug the HDMI cable from it.

---

