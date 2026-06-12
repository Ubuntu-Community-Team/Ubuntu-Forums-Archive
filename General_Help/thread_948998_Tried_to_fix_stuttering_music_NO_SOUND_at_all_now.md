---
title: "Tried to fix stuttering music: NO SOUND at all now"
date: 2008-10-15
forum: General Help
---

### Post by kpmoore on 2008-10-15
I'm very new to ubuntu (just installed it a few days ago) so please bear with me.

I have a Creative X-Fi. In order to get it to work, I followed this guide:
[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)
which involved recompiling a custom kernel. Worked like a charm.

Only problem was that my music was stuttering while the CPU was under load. I did a lot of research and determined that pulseaudio was the problem. I, therefore, followed this guide:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)
in hopes of fixing it. After completing the guide, the only sound I hear is the drum sound of the login screen. Beyond that, I can't get any sound to work.

Playing the test sound in the sound properties menu yields this error:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument*

Trying to play a song in rhythmbox yields a similar error:
* Failed to connect stream: Invalid argument*

I had the problem before, and I fixed it by changing all the sound properties from "Autodetect" to ALSA. The pulseaudio guide had me change them back to Autodetect, however changing them back to ALSA now doesn't change anything.

Here's where it gets weird. I tried killing pulseaudio ("pulseaudio -k") and now the test sounds work. However, my music collection now sounds TERRIBLE. Lots of static and scratching sounds. 

[UPDATE] I just tried a youtube video, sound works perfectly (this is still after killing pulseaudio). I tried to start pulseaudio again ("pulseaudio") and I got the following output:
[I]W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted[/I]


Can you help me get my sound back?

---

