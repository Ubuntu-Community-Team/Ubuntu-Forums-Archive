---
title: "Can I use a P3 1Ghz to Stream DVD's on my Network with VLC?"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by caffienda on 2007-02-27
I have 2 extra P3 1Ghz Dell PC's.  One with 512Mb Ram & 60GB HD, the other with 128 MB RAM and 40Gb HD. 

I was wondering if I could use these to stream ripped DVD's over my network.  Actually I would also like to stream my recordings from my PVR.  

The DVD's are ripped from to 1GB vob files.  I also have 4-8GB ISO files.   What is the best way for me to host these files.  Something as simple as samba or NFS?  Isn't VLC used to host streaming media?

Would these machines be better used as clients, to receive the video stream?

---

### Post by tgalati4 on 2007-02-27
Having set up multi-media servers, I would say that a PIII is good for general file serving and music/mp3 serving.  Gnump3d is a great little Perl program that serves movies and music files locally or over the internet (when you are at work for instance and you want to listen to your music.)

For video, you need more horsepower.  Core2 Duo and lots of RAM.  Any swapping and you will get stutters, which is unacceptable.  Your network connectivity is important.  Good quality cabling and professional quality routers.

I was able to get wireless A to work at high bandwidth for short video stints (high def movies trailers, music videos) where a dropped frame or two is not too noticeable.  Watching a full length movie would cause problems with losing audio sync (once lost, it's often not recovered without restarting and recuing--a real pain).

You could try running Dynebolic which is a realtime kernel which guarantees 95% of the cpu cycles go to your selected application.  I have only used it for recording, compressing to mp3 and streaming audio files.  A PIII is acceptable for audio, not sure about video.  My guess is you can do it, but it won't be pretty.

Seach MythTV and you will get an idea of what kinds of boxes people are putting together to watch video.

Good luck.

---

### Post by caffienda on 2007-02-28
Thanks for the info.  If the entire movie were to be copied to the computer before viewing, I would think this would eliminate a lot of the problems..  Then it would be like putting in a DVD.  I know a P3 1Ghz can handle that no problem.  I was watching DVD's on my old P2 400mhz back in the day!

---

