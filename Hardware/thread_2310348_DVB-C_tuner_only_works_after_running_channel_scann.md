---
title: "DVB-C tuner only works after running channel scanning tool"
date: 2016-01-18
forum: Hardware
---

### Post by PrinceVince on 2016-01-18
I've recently configured my DVB-C tuner card, a TechnoTrend Budget C2-4500 CI (Similar [DVBSky_T980C](https://www.linuxtv.org/wiki/index.php/DVBSky_T980C)). The card works fine (I use *mpv* to stream from the adapter), but what I didn't immediately notice is that it only worked in the session in which I had run a channel scan using a small tool called *w_scan*.

After a regular boot, the card is not accessible by *mpv* but briefly running *w_scan* "enables" it and everything works fine again.

Can anyone familiar with the topic suggest a way to get the card into an functioning state on boot? I don't know what *w_scan* does, but it sure doesn't require special privileges.

---

### Post by Bucky Ball on 2016-01-18
Well, it needs channels to show you anything, if you are intending to watch TV channels, that is. That is what you are talking about I presume?

You could try Me-TV (in the repos) if it is. That does an auto scan the first time you launch it and that is it. The channels are there in the channels.conf file on reboot and ever more. 

If you are watching TV, not sure what the 'streaming with MPV' part means. Sorry if I'm misunderstanding. I have a DVB-T dongle (in Australia) and I just plug it in, launch Me-TV and off I go. ;)

---

### Post by PrinceVince on 2016-01-18
No, the channels are there. The issue is that **mpv** can't access the adapter until I run **w_scan** (for a few seconds), which seems to have some hardware enabling effect.

---

### Post by Bucky Ball on 2016-01-18
Just wondering why you're using MPV to watch TV when there are apps available in the repos specifically for watching TV ... 

> mpv is a movie player based on MPlayer and mplayer2. It supports a wide
variety of video file formats, audio and video codecs, and subtitle types.

MPV is a multimedia player generally intended for watching movies (from a stream or a hard drive). Watching TV from a dongle is not that. 

If all you want to do is watch TV and getting this to work in MPV is not a project you are doing simply to learn, you are making it harder than it is. :)

---

### Post by PrinceVince on 2016-01-19
Turns out the issue lies with MPV, not the drivers as I had assumed. I like MPV a lot and worry about bloat so I was delighted to find out that I can just stream and record video with my favorite player. Many audio/video playback applications attempt to be "media centers" instead of simple tools focused on one task. But you're right, I'm making it harder than it needs to be by going this route.

---

### Post by Bucky Ball on 2016-01-19
Good that you reached a resolution. So, how did you end up achieving your goal?

---

